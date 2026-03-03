The Problem: Full Table Scans
Without an index, a database must perform a full table scan, checking every single row to find a match.
Linear Growth: While fast on small tables, performance degrades linearly as the table grows, leading to slow API responses during peak traffic.
Redundant Work: Even if a match is found early, the database continues scanning the remaining millions of rows because it doesn't know if other matches exist.
The Core Structure: B-Trees and B+ Trees
Most relational databases (Postgres, MySQL, SQL Server, Oracle) use a B-tree (or more specifically, a B+ tree) as their foundational data structure.
Wide and Shallow: Unlike a binary tree, which would require many disk reads, a B-tree is designed to be shallow (only 3-4 levels deep for 10 million entries).
Page-Aligned: Nodes are sized to match disk pages (typically 8-16 KB), so each level of the tree costs exactly one disk read.
Leaf Node Chaining: In a B+ tree, leaf nodes are linked in a sorted chain, allowing the database to perform range queries (e.g., finding all dates between two points) efficiently by walking forward through the leaves.
Composite Indexes and Column Order
A composite index covers multiple columns, but its utility depends entirely on column order, a concept known as the leftmost prefix rule.
The Phone Book Analogy: A phone book sorted by "Last Name, then First Name" is useless if you only know the first name. Similarly, a composite index is only efficient if you filter by the leading columns in order.
Skip Scans: Some modern databases can attempt a "skip scan" to use trailing columns, but this is a fallback and is consistently outperformed by a well-ordered index.
Design Strategy: You should generally put equality conditions first and range conditions last to keep the scanned range as tight as possible.
Covering Indexes and Lookups
When a database finds a row in an index, it often has to go back to the main table to fetch columns not stored in the index; this is known as a bookmark lookup or heap fetch.
The Cost of Lookups: If a query returns many rows, these random disk reads can become so expensive that the query planner might ignore the index and choose a full table scan instead.
Covering Indexes: An index that includes every column requested by the query (including those in SELECT, ORDER BY, and GROUP BY) allows the database to skip the table lookup entirely.
Include Clause: Some databases allow you to attach extra columns as "payload" in the leaf nodes without adding them to the sort key, making the index "covering" without changing its structure.
The Cost of Indexing: Writes and Memory
Indexes are not "free"; they come with significant overhead:
Write Performance: Every INSERT, UPDATE, or DELETE requires updating every index on that table. A table with 12 indexes turns one write operation into 13 separate writes.
Memory Pressure: Indexes compete for space in the buffer pool (RAM). If too many indexes exist, they won't fit in memory, forcing the database to read from disk—the very problem indexes were meant to solve.
When to Avoid or Remove Indexes
Low Cardinality: Indexing a column with very few distinct values (like a "status" column with three options) is often useless because the database still has to perform millions of lookups.
Partial Indexes: For columns where most values are the same, you can create a partial index that only covers the rare, frequently-searched values.
Unused Indexes: Databases track index usage. You should periodically check system stats (like pg_stat_user_indexes in Postgres) and drop indexes that have zero scans.
Strategic Best Practices
Use EXPLAIN ANALYZE: Before adding an index, check the query plan to see exactly where the time is being spent.
Analyze the Query: Identify which columns appear in WHERE, JOIN, ORDER BY, or GROUP BY to find candidate columns for indexing.
Regular Audits: Queries and features change over time; an index added for a defunct report still costs the system on every write.
