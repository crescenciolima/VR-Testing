# Test Case - Security

**Project:** Educational Metaverse – Battle of Itaparica (Decolonial Perspective)  
**Platform:** Desktop Web Browser (via Spatial.io WebGL client)  
**Attribute:** Security (ISO/IEC 25010)  
**Sub-attributes:** Confidentiality, Integrity, and Non-repudiation  

---

### Objective

Verify data **Integrity** and **Confidentiality** by ensuring that unauthorized network requests attempting to alter a student's quiz scores or intercept profile data are blocked, while validating that all critical actions generate an unalterable security log (**Non-repudiation**).

---

### Steps

1. **Intercept Session Traffic:** Open the metaverse in a desktop web browser (e.g., Google Chrome), open the browser's Developer Tools (Network tab), or route traffic through a local proxy tool (e.g., OWASP ZAP or Burp Suite). 
2. **Establish Data Baseline:** Log in with a standard student account, complete a quiz with a legitimate score of 70%, and locate the HTTPS POST request sent by the Spatial.io/Unity WebGL client to the cloud database updating the student's progress.
3. **Attempt Score Tampering (Integrity Attack):** Intercept the progress-saving network payload and attempt to maliciously modify the JSON parameters (e.g., change `"quiz_score": 70` to `"quiz_score": 100` and alter the account ID to overwrite another student's profile). Replay the modified request to the server.
4. **Attempt Unauthorized Access (Confidentiality Attack):** Attempt to access the cloud progress API endpoint directly without a valid JSON Web Token (JWT) or session cookie to see if other students' historical progress can be queried.
5. **Audit Security Logs (Non-repudiation Check):** Access the backend administration console or cloud database audit trail to check the logs generated during these actions.

---

### Expected Result

* **Integrity Protection:** The server rejects the manipulated network request with an HTTP 400 or 403 Forbidden error because the payload checksum or server-side validation detects tampering. The student's score remains 70% in the database.
* **Confidentiality Protection:** The API blocks any unauthenticated request to profile data, returning an HTTP 401 Unauthorized error, successfully shielding private student metrics.
* **Non-repudiation:** The backend logging system automatically generates a secure, timestamped audit log entry detailing the student's account ID, IP address, the specific event (quiz completion), and a separate security alert log for the blocked unauthorized tampering attempt.