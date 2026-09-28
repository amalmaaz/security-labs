# SQL Injection — DVWA

**Target:** Damn Vulnerable Web Application (Docker: `vulnerables/web-dvwa`)
**Environment:** Kali Linux (VirtualBox)
**Security level:** Low

## Objective
Practice identifying and exploiting SQL injection vulnerabilities using
multiple techniques against DVWA's SQLi and Blind SQLi modules.

## Techniques Used

### 1. Classic SQL Injection
- **Payload:** `' OR '1'='1`
- **Result:** Bypassed the query logic and returned unintended data,
  confirming the input was not sanitized before being placed into the
  SQL query.

### 2. Error-Based SQL Injection
- **Payload:** `' AND extractvalue(1, concat(0x7e, (SELECT database())))-- -`
- **Result:** The application's verbose error message leaked internal
  database information (e.g. the current database name) directly in the
  response, confirming the query structure and giving a channel to
  extract data via forced SQL errors.

### 3. UNION-Based SQL Injection
- **Steps:**
  1. Determined the number of columns using `' ORDER BY N-- -`,
     increasing N until an error appeared.
  2. Used `' UNION SELECT null, @@version-- -` to confirm which column(s)
     reflect output.
  3. Extracted data with a payload such as:
     `' UNION SELECT user, password FROM users-- -`
- **Result:** Retrieved usernames and password hashes directly in the
  page output by appending a second query whose results were displayed
  in the same table.

### 4. Blind SQL Injection
- **Boolean-based:**
  - True condition: `' AND 1=1-- -` → normal page response
  - False condition: `' AND 1=2-- -` → different/altered response
  - Used the difference in application behavior to infer true/false
    answers about the database one bit at a time.
- **Time-based (used where no visible difference existed):**
  - Payload: `' AND IF(1=1, SLEEP(5), 0)-- -`
  - A 5-second delay confirmed the condition was true, since there was
    no other observable output difference.

## Key Takeaways
- User input was concatenated directly into SQL queries without
  parameterization, making all four injection types possible.
- Error messages exposed internal database structure, which sped up
  exploitation significantly compared to blind techniques.
- Blind SQLi is slower and requires automation (e.g. sqlmap) at scale,
  but is a critical skill since many real-world apps suppress error
  output.

## Mitigation (for reference)
- Use parameterized queries / prepared statements.
- Apply least-privilege database accounts.
- Disable verbose error messages in production.
- Implement input validation and a WAF as defense-in-depth (not a
  substitute for fixing the query layer).
