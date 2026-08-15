# Task 3: SQL Injection — Low Security

**Objective:** To attack a vulnerable website (DVWA) on a local server to understand how SQL Injection works, test different payloads, and learn how to remediate the vulnerability.

## What is SQL Injection?
SQL Injection (SQLi) is a critical web vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It allows attackers to view data that they are not normally able to retrieve, such as user details, passwords, or other sensitive company data.

## Attack Execution & Payloads
The target environment was DVWA (Damn Vulnerable Web Application) running locally via XAMPP, with the security level set to **Low**.

**Payload 1 (Authentication Bypass / Data Leak):**
`' OR '1'='1`
*   **Why it worked:** The single quote (`'`) closes the developer's original SQL query prematurely. The `OR '1'='1` condition creates a statement that is always universally true (since 1 always equals 1). Because the database evaluates this as true, it bypasses the need for a valid password and dumps all the user records in the table.

*(Check the attached screenshot for the successful execution of this payload).*

## Remediation (How to Fix It)
To prevent SQL injection, developers should never trust user input directly in SQL queries. 
The most effective way to stop this is by using **Prepared Statements (Parameterized Queries)**. This ensures that the database treats user input strictly as data/text, and not as executable SQL code, completely neutralizing injection payloads.
