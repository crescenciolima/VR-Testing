# Test Case – Security

## Objective

Demonstrate that:

* Profile and progress data are transmitted in encrypted form (**Confidentiality**).
* APIs prevent unauthorized reading or modification of rankings and saved data (**Integrity**).
* All access and modification attempts are recorded with user identity, timestamp, and IP address (**Non-Repudiation**).

---

## Preconditions

* Production server running with HTTPS (TLS 1.2+).
* Two valid user accounts:

  * `StudentA` (owner of the progress data).
  * `StudentB` (third party).
* Tools:

  * Burp Suite (intercepting proxy).
  * mitmproxy with a forged certificate.
  * Postman.
  * Read-only access to security logs (Kibana or equivalent).
* Chrome 124 browser on a desktop machine (where the proxy will be configured).

---

## Steps

### 1. Confidentiality in Transit

a. Configure Chrome to use the Burp Suite proxy with a forged certificate.

b. Log in as `StudentA`.

c. Attempt to decrypt the session by inspecting whether any API endpoint accepts insecure connections, rejects TLS, or allows protocol downgrades.

### 2. Unauthorized Read Attempt

a. While authenticated as `StudentA`, capture the JWT token.

b. Using Postman, send the following request:

```http
GET /api/v1/profile?user=StudentB
```

using `StudentA`'s token.

c. Record the response code and response body.

### 3. Ranking Manipulation Attempt

a. Using the same token, send the following request:

```json
POST /api/v1/leaderboard

{
  "score": 999999
}
```

b. Query the leaderboard again using:

```http
GET /leaderboard/top10
```

to verify whether the fraudulent score was applied.

### 4. Non-Repudiation Verification

a. Access the security log dashboard.

b. Filter logs by `StudentA`'s user ID and the timestamp corresponding to Step 3.

c. Confirm the existence of an event such as:

> "Invalid update attempt"

containing:

* User ID
* IP address
* Endpoint
* Payload hash
* Result code (403/400)

---

## Expected Result

### Confidentiality

* All traffic uses TLS 1.2 or higher.
* Man-in-the-middle (MITM) attempts are blocked or result in certificate validation errors on the client.
* No sensitive information is visible in plaintext.

### Unauthorized Read Attempt

* The server returns **403 Forbidden** or **401 Unauthorized**.
* No information belonging to `StudentB` is disclosed.
* A denied-access event is recorded in the security logs.

### Ranking Manipulation Attempt

* The server returns **400 Bad Request** or **403 Forbidden**.
* The leaderboard remains unchanged (maximum legitimate score remains below `999999`).
* `StudentA`'s save-data hash remains identical to its previous value.

### Non-Repudiation

* A unique log entry exists containing:

  * UTC timestamp.
  * `StudentA` user ID.
  * Proxy IP address.
  * Target endpoint.
  * Result status code.

* An auditor can independently verify that the unauthorized modification attempt occurred.

---

## Approval Criteria

The test is **approved** if all of the above criteria are met.

The build is **rejected** if any of the following occur:

* Sensitive data is exposed.
* Unauthorized modifications are accepted.
* Security logs are missing, incomplete, or insufficient to prove the attempted action.
