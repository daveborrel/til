# ACID Properties

Transaction - A collection of operations (reads and writes) associated with a single logical operation.

In transaction processing, ACID properties help determine if that action is completed or rolled back.

Example:

A bank customer transferring $200 from chequing to savings account. Although this is one transaction, it is composed of the following steps:

1. Checking if the funds exist in the account
2. Deducting $200 from that account.
3. Adding $200 to that checking account.
4. Verifying the final balance.

**A - Atomicity**
- A transaction is treated as a single unit. Either it is successful or not.
    - Lets you retry the transaction without worry.

**C - Consistency**
- The transaction must preserve the consistency of the underlying data. No changes can violate the constraints placed on data.
    - Relationships between tables remain consistent, determine by the user.

**I - Isolation**
- A transaction is isolated from other transactions. Lets say someone wanted to withdraw from that same chequing account while they are transferring from that first account, the second transation would not fire until that transfer is complete.
    - Avoids dirty reads and writes.

**D - Durability**
- Any changes that are made will remain permanent.

### How Relational Databases Provide ACID Properties

DBMS like MySQL, PostGresSQL and Oracle have ACID guarantees out of the box.

### Sources
['ACID (atomicity, consistency, isolation, and durability)'](https://www.techtarget.com/searchdatamanagement/definition/ACID)
['ACID Databases – Atomicity, Consistency, Isolation & Durability Explained'](https://www.freecodecamp.org/news/acid-databases-explained/)
['What’s the Difference Between an ACID and a BASE Database?'](https://aws.amazon.com/compare/the-difference-between-acid-and-base-database/#:~:text=in%20the%20application.-,When%20to%20use:%20ACID%20compared%20with%20BASE,access%20to%20the%20product%20price.)