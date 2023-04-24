# Oracle Recipe #1: How to generate an IDENTITY column using a sequence

Primary keys can be created using either numeric or character data types, with one exception: Oracle does not have the same concept of identity columns as MS SQL Server.

What is an Identity Column?
It is a property that automatically generates a unique sequential value when it is assigned to a numeric data type. Oracle handles this concept using a database object called sequence.

The Sequence database object enables you to generate a unique sequence number. Each user of the sequence can increment it and obtain numbers for their use. Because multiple users can obtain sequence numbers, there is no guarantee that the numbers you get will not have gaps.

A sequence does not have to be related to a single table, and therefore could be used to provide unique numbers to multiple tables. As a general rule, having one sequence per table or at least one for each major table results in easier diagnostics and a better overall experience. The following examples show how you can add an identity column for two tables: categories and publishers.

Each table will use a IDENTITY column as PRIMARY KEY.
Fig 1. The categories and publishers catalog.



Fig 2. Script to create both tables.



The following code shows an example of how to select the NEXTVAL from a sequence. Upon executing this trigger, the sequence value is incremented by 1.

Fig 3. Script to create database objects: triggers and sequences.



Each time we add a new row, the trigger will automatically create a new unique number for that row. With this concept, the first row ID would be 1, and the next ID would be last ID number plus one.

Fig 4.Querying the tables.



Download Scripts
