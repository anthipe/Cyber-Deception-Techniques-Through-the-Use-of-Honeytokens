## Honeytoken Datasets (SQL Dumps)

The project includes three primary SQL dump files. These represent the "snapshots" used to evaluate how different honeytoken placements affect detection:

first_chat (Snapshot 1): This file contains the initial integration of the accounts table. It includes a mix of real employee data and synthetic accounts with hashed passwords acting as honeytokens.

second_chat (Snapshot 2): This version extends the honeytoken footprint by adding synthetic records to the employees table. It establishes relational consistency between the accounts and employees tables to enhance realism.

third_chat (Snapshot 3): adds synthetic transactional data to the orders.