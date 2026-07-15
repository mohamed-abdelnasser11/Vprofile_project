# VProfile Project

VProfile is a Java web application built with Spring MVC and deployed in a multi-tier environment using VirtualBox and Vagrant. The project demonstrates how a full application stack can be provisioned across multiple virtual machines, including a database, cache server, message broker, application server, and web server.

## Project Overview

This project is a sample web application that provides user registration, login, profile management, and other account-related features. It is designed to show how modern web applications can be deployed in a distributed infrastructure using infrastructure automation.

## Architecture

The application is deployed across several VMs:

- DB VM: hosts the MySQL database and imports the application schema/data
- Memcached VM: provides in-memory caching
- RabbitMQ VM: handles messaging services
- App VM: runs the Java application on Tomcat
- Web VM: serves traffic through Nginx

This setup helps simulate a realistic production environment where different services are separated across machines.

## Technologies Used

- Java / Spring MVC
- Spring Security
- Spring Data JPA
- Maven
- JSP
- Tomcat
- MySQL
- Memcached
- RabbitMQ
- Nginx
- Vagrant
- VirtualBox

## Prerequisites

Before using this project, make sure you have:

- JDK 17 or 21
- Maven 3.9+
- MySQL 8
- VirtualBox installed
- Vagrant installed

## Database

The project uses MySQL as its main database. The SQL dump file is located at:

- [src/main/resources/db_backup.sql](src/main/resources/db_backup.sql)

To import it into MySQL, use:

```bash
mysql -u <user_name> -p accounts < db_backup.sql
```

## Deployment Options

### 1. Automated Provisioning

The automated folder creates VMs and provisions them automatically using shell scripts.

Path:
- [vagrant/Automated_provisioning_WinMacIntel](vagrant/Automated_provisioning_WinMacIntel)

This option is useful when you want Vagrant to create and configure all machines automatically.

### 2. Manual Provisioning

The manual folder creates the VMs without automatic provisioning. It is useful when you want to configure each server manually.

Path:
- [vagrant/Manual_provisioning_WinMacIntel](vagrant/Manual_provisioning_WinMacIntel)

## How Vagrant Deploys the Project

Vagrant is used to create multiple virtual machines on VirtualBox. Each VM is assigned a role:

- db01: database server
- mc01: memcached server
- rmq01: RabbitMQ server
- app01: application server running Tomcat
- web01: web server running Nginx

With this approach, the application can be deployed in a distributed environment that resembles a real production setup.

## How to Run

### Automated deployment

```bash
cd vagrant/Automated_provisioning_WinMacIntel
vagrant up
```

### Manual deployment

```bash
cd vagrant/Manual_provisioning_WinMacIntel
vagrant up
```

## Summary

This project demonstrates a complete DevOps-style deployment workflow using Vagrant, VirtualBox, and multiple virtual machines. It shows both automated and manual provisioning approaches for deploying the same application across different environments.


