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
    - Its key characteristics are that it has a predefined schema (rows and columns) and high data integrity via keys and constraints. It is easily searchable and queryable using SQL, and it follows Schema-on-Write.
    - Most common examples are RDBMS tables (MySQL, PostgreSQL, Oracle), spreadsheets (Excel), banking transactions, inventory systems.
    - For the purpose of storage and tools, it uses Relational Databasaes and Data Warehouses.
2. **Unstructured Data:**
   - Data that lacks any predefined conceptual model, format, or organizational schema.
   - Its key characteristics are having no fixed format or tabular structure, accounting for the vast majority of generated data, and carrying a high storage footprint. It follows Schema-on-Read and requires specialized processing techniques like Natural Language Processing (NLP), Computer Vision, or text mining.
---
   - Most common examples are text documents (PDF, Word), multimedia files (images, MP4 videos, audio), social media content, and IoT sensor feeds.
 - For the purpose of storage and tools, it uses Distributed File Systems (HDFS), Data Lakes, and Object Stores (like AWS S3).
3. **Semi-Structured Data:**
   - Data that does not conform to a rigid relational schema but contains tags, markers, or internal keys to segregate data elements.
   - Its key characteristics are a flexible schema where fields can vary per entry, a self-describing hierarchical tree-like structure, and storage primarily as key-value pairs or documents. It is more manageable to query than unstructured data and is typically navigated using path-based tools like XPath or JSONPath.
   - Most common examples are JSON files, XML documents, emails (structured headers/metadata with text bodies), and server or application log files.
   - For the purpose of storage and tools, it uses NoSQL Databases (such as MongoDB, CouchDB) and XML/JSON file repositories.
---
# <span style="color: #bf4300;">Evolution of Big Data</span>

The shift from centralized relational systems to distributed, cloud-native, and real-time streaming architectures.

```mermaid
graph LR
  RDBMS["RDBMS (1970s)"] --> DW["Data Warehouses (1990s)"]
  DW --> Hadoop["Hadoop & NoSQL (2000s)"]
  Hadoop --> Spark["Spark In-Memory (2010s)"]
  Spark --> Cloud["Cloud & Lakes (Modern)"]
```

## 1. Traditional Databases (1970s – 1980s)

- **Foundation:** Relational Database Management Systems (RDBMS) designed for structured data
- **Core Technology:** Fixed tabular format queried using Structured Query Language (SQL)
- **Key Guarantees:** Strict **ACID** transactions ensuring high data integrity
- **Examples:** Early Oracle, IBM DB2, Microsoft SQL Server

{reveal}
> **Bottleneck:** Relies purely on vertical scaling (scale-up) and rigid Schema-on-Write, failing when workloads explode.

---

## 2. Enterprise Data Warehousing (1990s)

- **Purpose:** Decoupled analytics repository optimized for Business Intelligence (BI)
- **Integration:** Consolidated historical data using scheduled batch **ETL** pipelines
- **Storage Model:** Dimensional modeling utilizing **Star** and **Snowflake** schemas
- **Processing:** Online Analytical Processing (OLAP) multidimensional queries

{reveal}
> **Bottleneck:** High licensing costs, multi-hour batch latency, and inability to handle semi-structured or unstructured formats.

## 3. The Big Data Explosion & Hadoop (Mid 2000s)

- **Growth Driver:** Web 2.0, search engines, and social media (Google, Facebook, YouTube)
- **Google Papers (2003–2004):** Introduced Google File System (GFS) and MapReduce
- **Apache Hadoop (2006):** Open-source distributed computing on commodity hardware clusters
  - **HDFS:** Fault-tolerant distributed storage with block replication
  - **MapReduce:** Distributed compute bringing execution to the data
- **NoSQL Movement:** Flexible schema stores adhering to BASE and CAP theorem (MongoDB, Cassandra, HBase)

---

## 4. In-Memory Computing & Streaming (2010s)

Hadoop's disk-bound MapReduce created heavy I/O latency during iterative processing.

- **Apache Spark (2014):** In-memory processing with Resilient Distributed Datasets (RDDs), up to 100x faster than MapReduce
- **Real-Time Stream Processing:** Continuous processing on data-in-motion with sub-second latencies
  - Apache Kafka
  - Apache Flink
  - Apache Storm
- **Target Use Cases:** Real-time fraud detection, dynamic pricing, and streaming recommendations

## 5. Cloud-Native & Data Lakehouses (Modern)

- **Decoupled Architecture:** Storage is fully decoupled from compute, enabling elastic scaling
- **Pipeline Evolution:** Shift from ETL to **ELT** (Extract, Load, Transform)
- **Data Lakes & Lakehouses:** Centralized object storage holding raw multi-format data using Schema-on-Read (Amazon S3, Google BigQuery, Snowflake)
- **AI Integration:** Massive distributed pipelines feeding deep learning and predictive ML models
---
# <span style="color: #bf4300;">Data Warehouse vs Database</span>
- A data warehouse is essentially a relational database at its core. Both of them use SQL as the query language.

- The major difference between a Data Warehouse and a Database is the type of data that they store and the way they store it.

- A simple example to understand a Data Warehouse can be: suppose there is a student in class 10th, and he has different notebooks for each subject; now say each notebook represents a Database for that subject. A Data Warehouse can be referred to as a bookshelf he has in his room, which stores all the notebooks he has had since he was in the first grade.

- Can refer to this video [https://www.youtube.com/watch?v=myi50Ccfbwo](https://www.youtube.com/watch?v=myi50Ccfbwo).
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

# <span style="color: #bf4300;">Challenges of Big Data</span>
1. **Lack of Knowledge Professionals:** Organizations face a shortage of skilled professionals who possess the necessary in-depth knowledge to effectively work within the Big Data domain.
2. **Lack of proper understanding of massive data:** Even when companies have skilled professionals, it becomes difficult for them to store, process, and understand data as it scales into massive data sizes.
---
3. **Data growth issues**: As Big Data grows over time, it creates a recurring loop of needing more hardware and higher financial investment to keep up with storage requirements.
4. **Confusion during Big Data Tool Selection**: Selecting the right tools for analysis and storage is complex. Incorrect choices often lead to wasted time, effort, and financial resources.
5. **Integrating data from a spread of sources**: Data arrives from various disparate sources—such as social media, emails, and customer logs—making it highly challenging to merge this information into a single, meaningful report.
6. **Securing the data**: Because organizations focus heavily on processing and storing data, security often becomes an afterthought. This makes it easier for attackers to target the data once it is transmitted across a network.
---
# <span style="color: #bf4300;">Characteristics of Big Data</span>
Originally, Big Data was defined by 3 characteristics; it was defined by 3 V's :

1. **Volume:** The first V of Big Data represents the sheer size of the data. Traditional data is measured in Gigabytes or sometimes in Terabytes, but Big Data is enormous; it is measured in Petabytes, sometimes even in Exabytes. Even for storing big data that cannot be done on a single node, a distributed system is used.

2. **Velocity:** The second V represents the speed at which the data is generated and needs to be processed. Traditional data was generated in small amounts at predictable speeds, but Big Data is generated in massive amounts at a continuous high speed; thus, it cannot be processed by traditional databases.

3. **Variety:** The third V represents the different forms and formats in which data is generated. Traditional databases primarily handle structured data stored in rows and columns. Big Data encompasses multiple formats, including structured, semi-structured (like XML, JSON, and server logs), and unstructured data (such as photos, videos, audio, and sensor streams), requiring schema-on-read architectures rather than fixed schemas.

---

### Extended V's of Big Data

As Big Data evolved beyond the original 3 V's, two more critical characteristics were added:

4. **Veracity:** The fourth V refers to the trustworthiness, quality, and accuracy of the data. Because Big Data is collected from diverse and uncontrolled sources—such as social media, web scraping, and IoT sensors—it often contains noise, inconsistencies, missing fields, or biases. Ensuring high veracity requires data cleaning, validation, and governance to prevent faulty analytical results.

5. **Value:** The fifth V represents the actual business insights, operational improvements, or economic benefit derived from analyzing the data. Merely storing huge amounts of raw data provides no practical utility; the real significance of Big Data lies in transforming that raw information into actionable decision-making, predictive models, and cost reductions.