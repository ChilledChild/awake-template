---
title: What is ACID Compliance?
subtitle: Defining database transactional standards
category:
  - Databases
author: Danny Child
date: 2021-05-05T19:18:30.692Z
featureImage: /uploads/jan-antonin-kolar-lrox0shwjuq-unsplash.jpg
---
ACID (atomicity, consistency, isolation, durability) are attributes about a database that ensures data validity throughout anticipated errors or failures. As a database performs a transaction, checks are performed by the database software to ensure that each point of data complies to predefined rules that relate to the transaction. ACID compliant databases are favored for handling large business critical data that may be historically referenced. An ACID compliant database should comply with these four attributes:

### **Atomicity**

An atomic transaction is the smallest unique transaction that can be performed with maintaining all relevant data. If a portion of data is missing, or part of an operation fails, then the transaction is prevented. If it were to write as the transaction occurred, or not roll back prior to the transaction, data inconsistency will occur.

### **Consistency**

When a transaction is executed, anywhere from one thousand to one million rows could be involved in each transaction. Regardless of the expected transaction result, all rules and actions must be consistent throughout the transaction. There are multiple models of consistency types including Casual, Eventual, or Strict Consistency. Each type is considered weaker or stronger to another, while favoring speed or reliability.

### **Isolation**

Multiple transactions and commands may be performed at the same time. Depending on the order of operation, specific operations may be performed sequentially while others are performed concurrently. Operations that are not isolated can lead to mixing rows of data, leading to data inconsistency and compromising the database.

### **Durability**

Durability of a database ensures that any performed transactions are guaranteed to be committed to the database, even through sudden errors or failure. Especially in a power outage, data will not be lost as it is written to the disk and is not dependent on memory processes.

# **Databases and ACID Compliance**

What happens when one of these attributes are missing in a database? MongoDB was found to not ensure ACID compliance, from research performed by Kyle Kingsbury. Kyle found that casual consistency was allowing nodes to read data before data is fully committed. As a result, data safety is not guaranteed, and written data can be lost, despite claiming ACID compliance. Had MongoDB claimed BASE compliance, the database community could have been more forgiving.
https://twitter.com/QuinnyPig/status/1264052819515998208
https://jepsen.io/analyses/mongodb-4.2.6

Databases like PostgreSQL are ACID compliant out of the box. However, it is the responsibility of the database admin that transactions are handled correctly across each node. Similar to AWS and cloud security, the platform provides the option for ACID compliance, but what’s done with the database is what makes it ACID compliant.

MySQL, one of the most popular SQL databases, is not ACID compliant on its own. MySQL first shipped with ISAM, which could not provide effective consistency, falling into the same trap that many other NoSQL databases meet. By integrating with InnoDB, services like Twitter and YouTube are able to take advantage of large transactions and quick read operations to serve millions of users.

Integrations like NodeJS allow for native interfacing with a NoSQL database, though effective data warehousing makes the difference to make a fast database while establishing data integrity. Reviewing methods from Kimball and Inmon provide solutions to OLTP vs OLAP data processing.

Meeting ACID compliance comes at the cost of computing resource and additional time for handling data. As computing resources become more available and cheaper to use, the upfront cost has less weight to the risk of time and potential error. If data is key to running a business, then removing the risk of data loss is eagerly met by a sound solution. As data becomes more complex, so do the needs of the system supporting that data.