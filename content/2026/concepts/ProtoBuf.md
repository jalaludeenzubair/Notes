### **Encoding (Server Side)**

1. Load the `.proto` description.
2. Convert the raw JSON data into Protobuf objects.
3. Encode them to bytes (`Uint8Array`) ready for transmission.

### **Decoding (Client Side)**

1. WebSocket sends binary data as a `Blob`.
2. Client converts it to `Uint8Array`.
3. Protobuf decoder turns it back into structured data

## **1️⃣ Primitive Data Types (Basic Building Blocks)**

- **Integers**
  - `int32`, `int64` → signed integers (negative numbers inefficiently encoded)
  - `uint32`, `uint64` → unsigned integers (only positive numbers)
  - `sint32`, `sint64` → signed integers with **zig-zag encoding** (efficient for negatives)
  - `fixed32`, `fixed64` → fixed-size integers (always 4 or 8 bytes)
  - `sfixed32`, `sfixed64` → fixed-size signed integers
- **Floating Point Numbers**
  - `float` → 32-bit floating point
  - `double` → 64-bit floating point
- **Boolean**
  - `bool` → `true` or `false`
- **Strings and Bytes**
  - `string` → UTF-8 encoded text
  - `bytes` → raw binary data (images, hashes, etc.)

---

## **2️⃣ Composite Data Types (Structured Data)**

- **Messages**
  - Fundamental unit in Protobuf
  - Can contain **primitive fields** or **other messages**
  - Supports **nested structures**
- **Enums**
  - Predefined set of **named constants**
  - Ensures safer, readable values instead of arbitrary integers
- **Repeated**
  - Field can appear **0 or more times**
  - Acts like an **array/list**
- **Map**
  - Key-value pair field
  - Key: integral or string types
  - Value: any scalar, enum, or message
- **Oneof**
  - Only **one of the fields can be set at a time**
  - Saves memory, prevents conflicting data

---

## **3️⃣ Usage Notes / Tips**

- Use **smallest data type** that fits your range → reduces size, increases speed
- Use **`sint32`/`sint64`** for negative-heavy integers
- Use **`fixed32`/`fixed64`** when predictable byte size is important
- `repeated` = arrays, `map` = objects/dictionaries, `oneof` = exclusive choice
- Messages + nested messages = great for **complex structured data**
- Enums make values readable and safe for logic checks
- `bytes` for raw data like images or serialized blobs
- Always maintain **consistent `.proto` schema** between server and client

---

## **4️⃣ MERN Stack Context**

- **Server (Node.js/Express)**
  - Encode JSON → Protobuf binary using these types
  - Send over WebSocket/HTTP
- **Client (React)**
  - Decode Protobuf binary → JS objects
  - Map `repeated` → arrays, `map` → objects
  - Handle `oneof` → conditional rendering
