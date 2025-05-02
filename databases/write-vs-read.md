# Write Heavy vs Ready Heavy Systems

### Read Heavy System

Have a high volume of read operations.

Examples include:

- Content Delivery Networks
- Reporting Systems
- Read-Intensive APIS

_Key Strategies_

- Caching
- Replication
- CDN
- Load Balancing
- Data Indexing

### Write Heavy System

- Logging Systems
- Real Time Data Collection
- Transactional Databases

_Key Strategies_

- Write Batching
- Command Query Responsibility Segregation - Seperate models for read and writes
- Event Sourcing
