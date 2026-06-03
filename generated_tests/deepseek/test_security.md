# Test Case – Security

## Objective

Verify that the metaverse adequately protects user data, prevents unauthorized manipulation, and maintains auditable logs for critical actions.

---

## Steps

1. Confidentiality Test (Data Protection)

- Perform network traffic analysis (using Wireshark or Burp Suite) to verify:
	- Whether login credentials (username/password) and cloud-stored progress data are transmitted via HTTPS/SSL.
	- Whether sensitive information (e.g., email addresses, quiz history) is exposed in requests or client-side logs.
- Attempt to access another user’s data by modifying URL parameters (e.g., .../user?id=2).

2. Integrity Test (Fraud Prevention)

- Use tools such as Cheat Engine or save-file modification techniques to:
	- Alter quiz scores.
	- Unlock content without meeting the required conditions.
	- Modify multiplayer rankings.
- Verify that the system:
	- Blocks local modifications that are not validated by the server.
	- Detects and reverses inconsistencies in cloud-saved data.

3. Non-Repudiation Test (Traceability)

- Perform critical actions (e.g., deleting progress, sending multiplayer messages) and verify:
	- Whether server logs accurately record the user ID, timestamp, and action performed.
	- Whether logs are immutable (e.g., stored in a database with timestamps and digital signatures).

---

## Expected Result

✅ Confidentiality

- All data is transmitted in encrypted form (HTTPS).
- Attempts to access another user’s data return a 403 Forbidden error.

✅ Integrity

- Unsynchronized local modifications are rejected by the server.
- Rankings and progress data are validated using checksums or digital signatures.

✅ Non-Repudiation

- Detailed logs are generated for critical actions and retained for 90 days (in compliance with Brazil’s LGPD).
- Log records include IP address, session ID, and timestamps for auditing purposes.

---

## Failure Criteria

❌ The test fails if:

- Data is transmitted in plain text (HTTP).
- Scores or rankings can be modified using external tools.
- Logs are incomplete or can be deleted by the user.

---

## Additional Notes

- Test in different environments (e.g., public Wi-Fi networks) to evaluate the risk of data sniffing.
- Simulate SQL injection attacks in login forms (e.g., the “Player Name” field).
- Verify compliance with LGPD requirements (e.g., the ability to permanently delete user data).

---

## Recommended Tools

- OWASP ZAP (web vulnerability testing).
- Fiddler (request and response analysis).
- SQLMap (database injection testing).