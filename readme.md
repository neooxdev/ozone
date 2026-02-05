# Ozone

Ozone is an **in-memory key-value database** with **durable write-ahead logging (WAL) via Kafka**. It ensures fast reads/writes and can rebuild state after crashes.

---

## Features

- Fast in-memory key-value store  
- Durable WAL using Kafka  
- Automatic recovery after failures  
- Simple `set`, `get`, `delete` API  

---

## Installation

```bash
git clone https://github.com/yourusername/ozone.git
cd ozone
# Build instructions here
```

---

## Usage

```python
from ozone import OzoneClient

db = OzoneClient("localhost:9092")
db.set("user:123", {"name": "Alice", "age": 30})
print(db.get("user:123"))
db.delete("user:123")
```

---

## Contributing

1. Fork the repo  
2. Create a branch: `git checkout -b feature/your-feature`  
3. Commit changes: `git commit -m "Add feature"`  
4. Push: `git push origin feature/your-feature`  
5. Open a Pull Request  

---

## License

MIT License – see [LICENSE](LICENSE)
