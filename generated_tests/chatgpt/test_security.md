# Test Case – Security

## Objective

Verify that user data (profile and progress) is protected against unauthorized access (confidentiality), cannot be improperly modified (integrity), and that actions performed within the environment are properly recorded in logs (non-repudiation).

---

## Steps

1. Access the metaverse as an authenticated student and generate progress by completing a minigame and answering a quiz.
2. Attempt to access another authenticated user's progress data by manipulating requests using a tool such as Postman or browser Developer Tools (DevTools).
3. Attempt to modify the ranking value locally (e.g., by manipulating a JSON response or injecting code through the browser console) and submit the altered data to the server.
4. Verify that the system generates and stores logs of user actions (login/access, quiz completion, progress saving) including date, time, and user ID.

---

## Expected Result

- The system blocks any attempt to access another user's data (e.g., returns 403 Forbidden or redirects the request appropriately).
- Attempts to manipulate data (ranking or progress) are rejected by the server; invalid values are not accepted and are recorded for auditing purposes.
- Actions performed within the environment are recorded in a secure log containing a timestamp, user ID, and activity description.
- Regular users cannot delete or modify log records.
- Profile and progress data are encrypted in transit (HTTPS) and, ideally, encrypted at rest.