# Database Deception: Design and Evaluation of Honeytokens in Relational Databases
This repository contains the experimental infrastructure and datasets for my undergraduate thesis at the University of Thessaly. The project focuses on proactive defense through cyber deception, specifically the implementation of honeytokens within a MySQL environment.

## Overview
The goal of this research is to evaluate how the placement and structure of honeytokens affect the detection of unauthorized access in relational databases. We utilize a containerized environment to expose a vulnerable database to the internet and monitor malicious interactions.

## Tech Stack
Docker & Docker Compose: For service orchestration and environment isolation.

MySQL 5.7: The core relational database management system (DBMS).

PHP: Powers the authentication interface (Login Page).

CTGAN & LLMs (ChatGPT/Gemini): Used for generating and optimizing high-fidelity synthetic data (honeytokens).

Wireshark: For deep packet inspection and network traffic analysis.

## Technical Implementation & Credits

While the honeytoken generation logic and database architecture are original research components, the web interface was built upon a baseline containerized application.

Web Interface: Based on the https://github.com/anveshmuppeda/docker-login-page.git by @anveshmuppeda.

Modifications:

Integrated a custom PHP-based Audit Logging system to track username, success status, and login_time .

Configured Docker Compose to link the web service with isolated MySQL instances (login_net and extra_net) .

Implemented Intentional Vulnerabilities to attract automated bot activity for research purposes .

## Architecture
The system consists of three main containers:

Web Entry Point (PHP): A login interface exposed on Port 80.

Primary DB (MySQL): Stores application logs and the logins table on Port 3307.

Extra-DB (MySQL): An isolated instance on Port 3306 containing the 3 database snapshots with honeytokens.

## Database Snapshots
We implemented three versions of the Northwind database [https://docs.yugabyte.com/stable/sample-data/northwind/]:

Snapshot 1: Added an accounts table with synthetic credentials (hashed passwords).

Snapshot 2: Integrated honeytokens into the employees table.

Snapshot 3: Extended honeytokens to the orders table to simulate transactional data exfiltration targets.

## Installation & Usage
Clone the repository:

Launch the environment:

Access the Login Page: Open http://localhost:80 in your browser.

## Key Findings
Bot Dominance: 97.8% of external traffic originated from automated tools (bots) rather than human attackers.

Targeting: Port 3306 received 88.4% of all network packets, indicating a preference for direct DBMS attacks.

Attacker Behavior: Captured logs revealed attempts at SQL Injection, Path Traversal, and Privilege Escalation (GRANT ALL PRIVILEGES).

> [!CAUTION]
This project contains intentional vulnerabilities for research purposes.\
> DO NOT use default passwords (e.g., password1, password2, password3, password4) in a production environment.\
> DO NOT expose this infrastructure to the public internet without proper monitoring.

### Thesis Committee
Student: Petridou Anthi

Supervisor: 

University: University of Thessaly, Department of Computer Science and Biomedical Informatics
