
## The services on the Azure Data platform
## Structured data

In relational database systems like Microsoft SQL Server, Azure SQL Database, and Azure SQL Data Warehouse, data structure is defined at design time. Data structure is designed in the form of tables. This means it's designed before any information is loaded into the system. The data structure includes the relational model, table structure, column width, and data types.

Relational systems react slowly to changes in data requirements because the structural database needs to change every time a data requirement changes. When new columns are added, you might need to bulk-update all existing records to populate the new column throughout the table.

Relational systems typically use a querying language such as Transact-SQL (T-SQL).

## Nonstructured data

Examples of nonstructured data include binary, audio, and image files. Nonstructured data is stored in nonrelational systems, commonly called unstructured or NoSQL systems. In nonrelational systems, the data structure isn't defined at design time, and data is typically loaded in its raw format. The data structure is defined only when the data is read. The difference in the definition point gives you flexibility to use the same source data for different outputs. Nonrelational systems can also support semistructured data such as JSON file formats.

The open-source world offers four types of NoSQL databases:

1.  **Key-value store**: Stores key-value pairs of data in a table structure.
2.  **Document database**: Stores documents that are tagged with metadata to aid document searches.
3.  **Graph database**: Finds relationships between data points by using a structure that's composed of vertices and edges.
4.  **Column database**: Stores data based on columns rather than rows. Columns can be defined at the query's runtime, allowing flexibility in the data that's returned performantly.

Now that we've reviewed data types, let's look at common data platform technologies that facilitate the storage, processing, and querying of these data types.
# Understand data storage in Azure Storage

-   5 minutes

Azure Storage accounts are the base storage type within Azure. Azure Storage offers a very scalable object store for data objects and file system services in the cloud. It can also provide a messaging store for reliable messaging, or it can act as a NoSQL store.

Azure Storage offers four configuration options:

-   **Azure Blob**: A scalable object store for text and binary data
-   **Azure Files**: Managed file shares for cloud or on-premises deployments
-   **Azure Queue**: A messaging store for reliable messaging between application components
-   **Azure Table**: A NoSQL store for no-schema storage of structured data

You can use Azure Storage as the storage basis when you're provisioning a data platform technology such as Azure Data Lake Storage and HDInsight. But you can also provision Azure Storage for standalone use. For example, you provision an Azure Blob store either as standard storage in the form of magnetic disk storage or as premium storage in the form of solid-state drives (SSDs).

The following definitions focus on Azure Blob storage.

## When to use Blob storage

If you need to provision a data store that will store but not query data, your cheapest option is to set up a storage account as a Blob store. Blob storage works well with images and unstructured data, and it's the cheapest way to store data in Azure.

## Key features

Azure Storage accounts are scalable and secure, durable, and highly available. Azure handles your hardware maintenance, updates, and critical issues. It also provides REST APIs and SDKs for Azure Storage in various languages. Supported languages include .NET, Java, Node.js, Python, PHP, Ruby, and Go. Azure Storage also supports scripting in Azure PowerShell and the Azure CLI.

## Data ingestion

To ingest data into your system, use Azure Data Factory, Storage Explorer, the AzCopy tool, PowerShell, or Visual Studio. If you use the File Upload feature to import file sizes above 2 GB, use PowerShell or Visual Studio. AzCopy supports a maximum file size of 1 TB and automatically splits data files that exceed 200 GB.

## Queries

If you create a storage account as a Blob store, you can't query the data directly. To query it, either move the data to a store that supports queries or set up the Azure Storage account for a data lake storage account.

## Data security

Azure Storage encrypts all data that's written to it. Azure Storage also provides you with fine-grained control over who has access to your data. You'll secure the data by using keys or shared access signatures.

Azure Resource Manager provides a permissions model that uses role-based access control (RBAC). Use this functionality to set permissions and assign roles to users, groups, or applications.
# Understand data storage in Azure Data Lake Storage

-   5 minutes

Azure Data Lake Storage is a Hadoop-compatible data repository that can store any size or type of data. This storage service is available as Generation 1 (Gen1) or Generation 2 (Gen2). Data Lake Storage Gen1 users don't have to upgrade to Gen2, but they forgo some benefits.

Data Lake Storage Gen2 users take advantage of Azure Blob storage, a hierarchical file system, and performance tuning that helps them process big-data analytics solutions. In Gen2, developers can access data through either the Blob API or the Data Lake file API. Gen2 can also act as a storage layer for a wide range of compute platforms, including Azure Databricks, Hadoop, and Azure HDInsight, but data doesn't need to be loaded into the platforms.

## Where to use Data Lake Storage Gen2

Data Lake Storage is designed to store massive amounts of data for big-data analytics. For example, Contoso Life Sciences is a cancer research center that analyzes petabytes of genetic data, patient data, and records of related sample data. Data Lake Storage Gen2 reduces computation times, making the research faster and less expensive.

The compute aspect that sits above this storage can vary. The aspect can include platforms like HDInsight, Hadoop, and Azure Databricks.

## Key features

Here are the key features of Data Lake Storage:

-   Unlimited scalability
-   Hadoop compatibility
-   Security support for both access control lists (ACLs)
-   POSIX compliance
-   An optimized Azure Blob File System (ABFS) driver that's designed for big-data analytics
-   Zone-redundant storage
-   Geo-redundant storage

## Data ingestion

To ingest data into your system, use Azure Data Factory, Apache Sqoop, Azure Storage Explorer, the AzCopy tool, PowerShell, or Visual Studio. To use the File Upload feature to import file sizes above 2 GB, use PowerShell or Visual Studio. AzCopy supports a maximum file size of 1 TB and automatically splits data files that exceed 200 GB.

## Queries

In Data Lake Storage Gen1, data engineers query data by using the U-SQL language. In Gen 2, use the Azure Blob Storage API or the Azure Data Lake System (ADLS) API.

## Data security

Because Data Lake Storage supports Azure Active Directory ACLs, security administrators can control data access by using the familiar Active Directory Security Groups. Role-based access control (RBAC) is available both in Gen1 and Gen2. Built-in security groups include ReadOnlyUsers, WriteAccessUsers, and FullAccessUsers.

Enable the firewall to limit traffic to only Azure services. Data Lake Storage automatically encrypts data at rest, protecting data privacy.
# Understand Azure Cosmos DB

-   5 minutes

Azure Cosmos DB is a globally distributed, multimodel database. You can deploy it by using several API models:

-   SQL API
-   MongoDB API
-   Cassandra API
-   Gremlin API
-   Table API

Because of the multimodel architecture of Azure Cosmos DB, you benefit from each model's inherent capabilities. For example, you can use MongoDB for semistructured data, Cassandra for wide columns, or Gremlin for graph databases. When you move your data from SQL, MongoDB, or Cassandra to Azure Cosmos DB, applications that are built using the SQL, MongoDB, or Cassandra APIs will continue to operate.

Note

For more information about the APIs that are available in Azure Cosmos DB, see  [Choose the appropriate API for Azure Cosmos DB storage](https://docs.microsoft.com/learn/modules/choose-api-for-cosmos-db/).

## When to use Azure Cosmos DB

Deploy Azure Cosmos DB when you need a NoSQL database of the supported API model, at planet scale, and with low latency performance. Currently, Azure Cosmos DB supports five-nines uptime (99.999 percent). It can support response times below 10 ms when it's provisioned correctly.

Consider this example where Azure Cosmos DB helps resolve a business problem. Contoso is an e-commerce retailer based in Manchester, UK. The company sells children's toys. After reviewing Power BI reports, Contoso's managers notice a significant decrease in sales in Australia. Managers review customer service cases in Dynamics 365 and see many Australian customer complaints that their site's shopping cart is timing out.

Contoso's network operations manager confirms the problem. It's that the company's only data center is located in London. The physical distance to Australia is causing delays. Contoso applies a solution that uses the Microsoft Australia East datacenter to provide a local version of the data to users in Australia. Contoso migrates their on-premises SQL Database to Azure Cosmos DB by using the SQL API. This solution improves performance for Australian users. The data can be stored in the UK and replicated to Australia to improve throughput times.

## Key features

Azure Cosmos DB supports 99.999 percent uptime. You can invoke a regional failover by using programing or the Azure portal. An Azure Cosmos DB database will automatically fail over if there's a regional disaster.

By using multimaster replication in Azure Cosmos DB, you can often achieve a response time of less than one second from anywhere in the world. Azure Cosmos DB is guaranteed to achieve a response time of less than 10 ms for reads and writes.

To maintain the consistency of the data in Azure Cosmos DB, your engineering team should introduce a new set of consistency levels that address the unique challenges of planet-scale solutions. Consistency levels include strong, bounded staleness, session, consistent prefix, and eventual.

## Data ingestion

To ingest data into Azure Cosmos DB, use Azure Data Factory, create an application that writes data into Azure Cosmos DB through its API, upload JSON documents, or directly edit the document.

## Queries

As a data engineer, you can create stored procedures, triggers, and user-defined functions (UDFs). Or use the JavaScript query API. You'll also find other methods to query the other APIs within Azure Cosmos DB. For example, in the Data Explorer component, you can use the graph visualization pane.

## Data security

Azure Cosmos DB supports data encryption, IP firewall configurations, and access from virtual networks. Data is encrypted automatically. User authentication is based on tokens, and Azure Active Directory provides role-based security.

Azure Cosmos DB meets many security compliance certifications, including HIPAA, FedRAMP, SOCS, and HITRUST.
# Understand Azure SQL Database

-   5 minutes

Azure SQL Database is a managed relational database service. It supports structures such as relational data and unstructured formats such as spatial and XML data. SQL Database provides online transaction processing (OLTP) that can scale on demand. You'll also find the comprehensive security and availability that you appreciate in Azure database services.

Important

This unit focuses on Azure SQL Database, the  _platform as a service_  (PaaS) database offering. Here we don't cover Microsoft SQL Server instances that are installed locally or within an Azure virtual machine (VM). Although these are similar, the configuration and benefits of Microsoft SQL Server differ from those of Azure SQL Database.

## When to use SQL Database

Use SQL Database when you need to scale up and scale down OLTP systems on demand. SQL Database is a good solution when your organization wants to take advantage of Azure security and availability features. Organizations that choose SQL Database also avoid the risks of capital expenditures and of increasing operational spending on complex on-premises systems.

SQL Database can be more flexible than an on-premises SQL Server solution because you can provision and configure it in minutes. Even more, SQL Database is backed up by the Azure service-level agreement (SLA).

## Key features

SQL Database delivers predictable performance for multiple resource types, service tiers, and compute sizes. Requiring almost no administration, it provides dynamic scalability with no downtime, built-in intelligent optimization, global scalability and availability, and advanced security options. These capabilities let you focus on rapid app development and on speeding up your time to market. You no longer have to devote precious time and resources to managing virtual machines and infrastructure.

## Ingesting and processing data

SQL Database can ingest data through application integration from a wide range of developer SDKs. Allowed programming languages include .NET, Python, Java, and Node.js. Beyond applications, you can also ingest data through Transact-SQL (T-SQL) techniques and from the movement of data using Azure Data Factory.

## Queries

Use T-SQL to query the contents of a SQL Database. This method benefits from a wide range of standard SQL features to filter, order, and project the data into the form you need.

## Data security

SQL Database provides a range of built-in security and compliance features. These features help your application meet security and compliance requirements like these:

-   Advanced Threat Protection
-   SQL Database auditing
-   Data encryption
-   Azure Active Directory authentication
-   Multifactor authentication
-   Compliance certification
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyOTc0MjczOTIsMTAxNjg1NjUzNSw1OT
k5MjM0MTVdfQ==
-->