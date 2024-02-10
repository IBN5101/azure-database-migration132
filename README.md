# (AiC03) Azure Database migration

Project prompt:

> In this project, you will architect and implement a cloud-based database system on Microsoft Azure, showcasing your hands-on expertise in cloud engineering.
>
> You'll begin by establishing a production environment database. Subsequently, you'll migrate the database to Azure SQL Database, focusing on crucial aspects like data backup, restoration, and automated scheduling. These efforts will strengthen your data management approach.
>
> A pivotal phase of the project involves simulating a disaster recovery scenario with potential data loss. Furthermore, you will explore the complexities of geo-replication and failover configuration to ensure data availability even uder challenging conditions.
>
> To enhance security, Microsoft Entra ID integration will be employed to define access roles, adding an extra layer of control and protection

This project is part of the Ai■■■■ skill bootcamp.

## Installation

(TBD)

## Usage

(TBD)

## File structure

(TBD)

## Comments

- The initial project setup was very simple and smooth. I definitely spent more efforts into personlizing the brand-new VM. As for SQL server and SSMS, the installation process took longer than expected.
- The production database restoration ran into a problem: I was unable to select the destination folder inside my user's Desktop. Workaround: placing the project folder directly on `C:\` folder.
- Setting up and connecting to the Azure SQL Database was easy. Schema migration and Data migration took significantly longer than I had expected.
- The backup process was rather meticulious but once you understand the process, it becomes much easier. The backup files are uploaded to Azure Storage for secure & online storage.
- One of the task was to create a separate VM for sandbox testing and to recover the database in this sandbox. After downloading the file from Azure Storage, it took only a few clicks to have the entire system fully replicated.
- A maintenance plan is also in place to fully backup the database every week, for a limited time.
- As for the Data Loss Simulation, the approach was to pick a random table and delete the top 1000 rows. This turned out to be the wrong approach because the product database is meticulously setup with many restrictions. For example: deleting records from `Person.Person` is not allowed due to REFERENCE constraint with `HumanResources.Employee`.
- After trials and errors, I successfully deleted the first 1000 records of the table `Production.WorkOrderRouting`. I confirmed the deletion by checking that the first ID of the table was 1339, while an unmodified backup showed the first ID of the table was 13.
- I restored the database on Azure and connected to it using Azure Data Studio. I noted that by selecting the target database while on the connection screen, it would fill in the necessary credentials to the Azure server and I only needed to change to the restored database. 

## License

Licensed under the [MIT](LICENSE.txt) license.
