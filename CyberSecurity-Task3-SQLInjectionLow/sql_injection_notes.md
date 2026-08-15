# SQL Injection Payload Log

**Target:** DVWA (Localhost)
**Module:** SQL Injection
**Security Level:** Low

## Payload Log

**Payload 1:** `' OR '1'='1`
* **Goal:** Database dump and authentication bypass.
* **Result:** Successful. The database returned the first names and surnames of all registered users (admin, Gordon Brown, Hack Me, Pablo Picasso, Bob Smith).
* **Explanation:** Injected a universal truth condition using the `OR` operator to manipulate the backend query into returning all rows.
