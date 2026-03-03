A **vector database** typically stores data in this form:

1. **ID**
   - A unique identifier for the record
   - Example: `"doc_1234"`
   - Used to retrieve, update, or delete the vector
2. **Vector (Embedding)**
   - A numerical array (usually float values)
   - Example: `[0.021, -0.887, 0.445, ...]`
   - Represents semantic meaning of text, image, audio, etc.
   - Used for similarity search (cosine similarity, dot product, Euclidean distance)
3. **Payload (Metadata)**
   - Additional structured information stored with the vector
   - Example:
     ```json
     {
       "title": "Introduction to AI",
       "author": "John Doe",
       "date": "2026-01-10",
       "category": "technology"
     }
     ```
   - Used for filtering, searching, and contextual retrieval

## 🔹 1. Cosine Similarity

- Measures **angle** between two vectors
- Ignores magnitude (length)
- Range: **-1 to 1**
  - 1 → most similar
  - 0 → unrelated
  - -1 → opposite

- Mostly used in **NLP / text embeddings**

## 🔹 2. Dot Product (Inner Product)

- Measures **direction + magnitude**
- Larger value → more similar
- If vectors are normalized → same as cosine similarity
- Used in **recommendation systems**

## 🔹 3. Euclidean Distance (L2)

- Measures **straight-line distance**
- Smaller value → more similar
- Sensitive to scale
- Used in traditional ML

`Length (or magnitude) of a vector = distance from the origin (0,0) to the point.`

## 🔎 Quick Difference

| Metric      | Measures       | Best For        |
| ----------- | -------------- | --------------- |
| Cosine      | Angle          | Text similarity |
| Dot Product | Angle + length | Recommenders    |
| Euclidean   | Distance       | Clustering / ML |
