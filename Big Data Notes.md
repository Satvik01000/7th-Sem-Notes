# <span style="color: #bf4300;">Introduction to Big Data</span>
<p style="font-size: 22px;">
Big Data refers to the massive amounts of data generated every day from various digital sources like social media, e-commerce, sensors, transactions, and more. As the volume of data grows exponentially, traditional data processing tools and databases cannot efficiently handle, store, or analyse such vast datasets.
</p>

**Big Data vs Traditional Data**
{reveal}
| Parameter | Traditional Data | Big Data |
| :--- | :--- | :--- |
| **Data Size** | Gigabytes (GB) to Terabytes (TB) | Terabytes (TB), Petabytes (PB), to Exabytes (EB) |
| **Data Types** | Primarily structured (tables, rows, columns) | Structured, semi-structured, and unstructured |
| **Architecture** | Centralized, vertical scaling (scale-up) | Distributed, horizontal scaling (scale-out / clusters) |
| **Processing** | Batch/sequential processing using RDBMS/SQL | Distributed/parallel processing (e.g., Hadoop, Spark) |
| **Schema** | Schema-on-write (strict schema before insert) | Schema-on-read (schema applied when querying) |

---
# <span style="color: #bf4300;">Types of Digital Data</span>
**<p style="font-size: 25px;">Digital data is of 3 types</p>**
1. **Structured Data:**
   - Data that can be stored, queried, and retrieved in a fixed, 
predefined format.
    - It's key characteristics are it has a predefined schema (rows and columns), high data integrity via keys and constraints. It is easily searchable and queryable using SQL and it follows Schema-on-Write.
    - Most common examples are RDBMS tables (MySQL, PostgreSQL, Oracle), spreadsheets (Excel), banking transactions, inventory systems.
    - For purpose of storage and tools it uses Relational Databasaes and Data Warehouses.
2. **Unstructured Data:**
   - Data that lacks any predefined conceptual model, format, or organizational schema.
   - Its key characteristics are having no fixed format or tabular structure, accounting for the vast majority of generated data, and carrying a high storage footprint. It follows Schema-on-Read and requires specialized processing techniques like Natural Language Processing (NLP), Computer Vision, or text mining.
---
   - Most common examples are text documents (PDF, Word), multimedia files (images, MP4 videos, audio), social media content, and IoT sensor feeds.
 - For purpose of storage and tools it uses Distributed File Systems (HDFS), Data Lakes, and Object Stores (like AWS S3).
3. **Semi-Structured Data:**
   - Data that does not conform to a rigid relational schema but contains tags, markers, or internal keys to segregate data elements.
   - Its key characteristics are a flexible schema where fields can vary per entry, a self-describing hierarchical tree-like structure, and storage primarily as key-value pairs or documents. It is more manageable to query than unstructured data and is typically navigated using path-based tools like XPath or JSONPath.
   - Most common examples are JSON files, XML documents, emails (structured headers/metadata with text bodies), and server or application log files.
   - For purpose of storage and tools it uses NoSQL Databases (such as MongoDB, CouchDB) and XML/JSON file repositories.
---
# <span style="color: #bf4300;">Evolution of Big Data</span>
The evolution of Big Data represents the transition from centralized, relational database systems handling small structured data to distributed, in-memory, and cloud-native frameworks capable of managing massive, multi-structured datasets in real time.

### 1. Traditional Databases and Data Warehousing (1970s – 2000s)
* **Relational Database Management Systems (RDBMS):** 
  - Emerged during the 1970s and 1980s using systems like Oracle, IBM DB2, and SQL Server to manage structured data in tables (rows and columns).
  - Leveraged Structured Query Language (SQL) for efficient retrieval, management, and ACID transaction guarantees.
* **Data Warehousing (1990s):**
  - Designed to aggregate and centralize structured historical operational data for reporting and Business Intelligence (BI).
  - Utilized Online Analytical Processing (OLAP) multidimensional cubes and batch Extract, Transform, Load (ETL) pipelines.
---
* **Technical Bottlenecks:**
  - Reliant on vertical scaling (scale-up), which became cost-prohibitive.
  - Strictly schema-on-write, rendering them incapable of ingesting high-velocity, semi-structured, or unstructured datasets.

# <span style="color: #bf4300;">Data Warehousing</span>
- A data warehouse is essentially a relational database at its core. Both of them use SQL as the query language.

- The major difference between a Data Warehouse and a Database is the type of data that they store and the way they store it.

- A simple example to understand a Data Warehouse can be: suppose there is a student in class 10th, and he has different notebooks for each subject; now say each notebook represents a Database for that subject. A Data Warehouse can be referred to as a bookshelf he has in his room, which stores all the notebooks he has had since he was in the first grade.
---
### 1. Type of Data:
- <span style="color: #bf4300;"> Standard Databases </span>  use OLTP (Online Transaction Processing), they are designed to store current, real-time data.
- Example: Consider a banking environment where a customer performs multiple transactions throughout the day. Every withdrawal, deposit, or fund transfer is captured and stored in the database immediately as it occurs 
- OLTP systems are optimized for fast writing and updating, prioritizing the efficiency of incoming data over query read speeds.
- <span style="color: #bf4300;"> Data Warehouses </span>  use OLAP (Online Analytical Processing), it stores the data with the intention that the data stored will be used for the purpose of analysis or reporting later.
- It is designed to store historical data, for example, a customer has been with the bank for 10 years. Now a Data Warehouse is used to store what the customer has been doing from day 1 until today. Basically, in simple terms, Data Warehouses store historical data; for example, if a bank wants to know what the customer has done over a period of time, or how the bank has performed over a period of time, they will use a Data Warehouse over a Database.
- OLAP systems are designed for faster reads; they may not necessarily have faster writes and updates.

---
### 2. How Data is stored:
- A <span style="color: #bf4300;"> Standard Databases </span> stores the data in Normal Form; this ensures there is no redundancy and no anomalies. This is the primary reason why databases have faster writes and updates but not faster reads, because now, for reading, queries have to have joins across multiple tables, which significantly reduces the performance of read queries.
- In <span style="color: #bf4300;"> Data Warehouses</span>, on the other hand, it is a common practice to store the data in denormalised form, or even if it is normalised, a minimal number of tables are preferred. This ensures that the data can be read in a really fast manner but it does cause redundancy.
- A data warehouse uses the concept of fact and dimension tables for the purpose of data storage; the fact table contains essential business information and requirements, whereas the dimension table stores the descriptive, detailed information.