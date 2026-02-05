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

## Project Structure

```text
ozone/
├── pom.xml                  # Maven build configuration and dependencies
├── README.md                # Project documentation
├── Makefile                 # Helper commands for build/run tasks
├── docker-compose.yml       # Runs Kafka and related services locally
│
├── src/                     # Main source code
│   ├── main/
│   │   ├── java/
│   │   │   └── com/ozone/
│   │   │       ├── Ozone.java            # Application entry point / server bootstrap
│   │   │       ├── store/                # Core in-memory key-value storage logic
│   │   │       │   ├── Store.java        # Main store implementation
│   │   │       │   └── KVEntry.java      # Key-value data model
│   │   │       ├── wal/                  # Write-Ahead Log (Kafka integration)
│   │   │       │   ├── WALManager.java   # Handles producing/consuming WAL events
│   │   │       │   └── WALEntry.java     # WAL record structure
│   │   │       ├── server/               # Networking layer
│   │   │       │   ├── TcpServer.java    # TCP server handling client connections
│   │   │       │   ├── RespProtocol.java # Protocol parsing (request/response format)
│   │   │       │   └── LRUCache.java     # In-memory cache for frequently used keys
│   │   │       └── RecoveryService.java  # Rebuilds store state from WAL after crash
│   │   └── resources/
│   │       └── ozone.properties          # Application configuration
│   │
│   └── test/                             # Test and benchmarking code
│       ├── java/
│       │   └── com/ozone/
│       │       ├── StoreTest.java        # Unit tests for key-value store
│       │       └── OzoneBenchmark.java   # Performance benchmarking
│       └── resources/
│           └── test.properties           # Test configuration
│
└── deploy/
    └── docker/
        └── Dockerfile                    # Docker image build instructions
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
