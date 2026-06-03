# Test Case – Reliability

## Objective

Verify that the metaverse maintains stable operation during normal use (maturity), continues to function acceptably after interruptions (fault tolerance), and correctly restores cloud-saved progress (recoverability).

---

## Steps

1. Access the metaverse through a desktop web browser, authenticate, and interact with the environment for 20 minutes (walk around, talk to NPCs, start a minigame, and complete a quiz).
2. During use, temporarily interrupt the internet connection (enable airplane mode or disconnect the network for 1 minute) and then restore it.
3. After reconnection, verify that the system resumes without freezing and restores the same saved state that existed before the disconnection (e.g., avatar position, ongoing minigame, completed quiz responses).
4. Repeat the test five times in separate sessions to measure stability and failure frequency.

---

## Expected Result

- The system does not experience critical failures (crashes or freezes) during normal use across all five sessions.
- After a connection loss, the metaverse displays a clear message to the user and automatically resumes operation when internet connectivity is restored.
- Cloud-saved progress is successfully restored, including the player's position, minigame status, and quiz responses.
- Recovery time after reconnection is ≤ 15 seconds.
- No significant data loss is observed after the interruption.