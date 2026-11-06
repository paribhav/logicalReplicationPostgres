# logicalReplicationPostgres

Hands-on Lab: PostgreSQL Logical Replication on Two Linux VMs
We will configure PostgreSQL Logical Replication (Publisher → Subscriber) using two Linux virtual machines.

This is a practical DBA lab covering installation, configuration, publication, subscription, data synchronization, monitoring, troubleshooting, and testing replication behavior.

The goal is to simulate a real production scenario where data from one PostgreSQL database is replicated to another server.

<img width="1006" height="908" alt="image" src="https://github.com/user-attachments/assets/b3317136-929a-4d37-8a73-e43f2ac45911" />


**Modify below paramters in postgresql.conf file on PUBLISHER server **

<img width="598" height="191" alt="image" src="https://github.com/user-attachments/assets/04cb1b0b-65c7-4e4e-8e14-321b21048141" />


**Parameter	                         Purpose**
wal_level	                    Enables logical WAL generation
max_wal_senders	Maximum       concurrent WAL sender processes
max_replication_slots	        Maximum replication slots
max_slot_wal_keep_size	      Limits WAL retained by a lagging slot

**Configure pg_hba.conf **
Configure pg_hba.conf with Subscriber server details.


<img width="716" height="172" alt="image" src="https://github.com/user-attachments/assets/0c779d94-fdee-4fc5-8fc8-2280cd89bb41" />


Restart PostgreSQL

<img width="1054" height="391" alt="image" src="https://github.com/user-attachments/assets/54a15680-b937-4441-9bf8-766ab5135d56" />

Verify changes either with grep command or login to postgres using SHOW command 

<img width="651" height="371" alt="image" src="https://github.com/user-attachments/assets/4dfadb7a-4674-432d-b649-452e5a1f2929" />

Create the replication user on Publisher
Grant access .

<img width="630" height="307" alt="image" src="https://github.com/user-attachments/assets/6232a7c8-e2d3-4c88-bebe-0c53e0f0607c" />

Create sourcedb ---> table ----> insert data 

<img width="721" height="400" alt="image" src="https://github.com/user-attachments/assets/76965038-85d3-4b7a-b709-303d5f07b1bb" />

Next step is to create  a Publication on Publisher --- WHY ? 
A publication acts as a control layer on the source database, defining the boundaries of what data can be replicated. Unlike physical streaming replication, which maintains an exact copy of the entire database, logical replication allows you to selectively publish specific tables and data changes, giving you granular control over what gets shared with subscriber databases.

<img width="892" height="283" alt="image" src="https://github.com/user-attachments/assets/a6b62c37-6528-4747-b15d-38ff94cd7b19" />

Note : We can configure /publish ALL tables or selected tables.





