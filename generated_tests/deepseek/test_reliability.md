# Test Case – Reliability

## Objective

Verify that the metaverse remains stable during prolonged use, recovers correctly after failures (such as connection loss), and properly restores cloud-saved progress.

---

## Steps

1. Maturity Test (Failures During Normal Use)

- Run the metaverse for 1 hour on browser, mobile, and VR platforms while performing frequent actions:
	- Navigating through the environment.
	- Interacting with NPCs.
	- Completing quizzes and minigames.
- Record occurrences of:
	- Crashes or freezes.
	- Visual or physics-related bugs.
	- Script failures (e.g., NPCs not responding).

2. Fault Tolerance Test (Unstable Connection)

- Simulate a connection loss during:
	- A dialogue with Maria Felipa.
	- Cloud progress saving.
	- An asynchronous multiplayer minigame.
- Verify that:
	- The system resumes normal operation after reconnection.
	- Data is not corrupted (e.g., partial progress is preserved).

3. Recoverability Test (Progress Restoration)

- Force an abrupt closure of the application (mobile/VR) or browser.
- Reopen the metaverse and verify that:
	- The last state is correctly restored (e.g., player position, completed quizzes).
	- Post-failure reload time is acceptable (≤ 10 seconds).

---

## Expected Result

✅ Maturity

- Zero crashes or critical failures during 1 hour of continuous use.
- No more than one minor bug (e.g., an unloaded texture) per session.

✅ Fault Tolerance

- After reconnection, the system:
	- Resumes dialogues from where they stopped.
	- Completes cloud saving without data loss.
	- Resumes multiplayer minigames or notifies the user about the disconnection.

✅ Recoverability

- Progress is fully restored after an abrupt shutdown.
- Reload time is ≤ 10 seconds on browser/mobile and ≤ 15 seconds on VR.

---

## Failure Criteria

❌ The test fails if:

- More than one crash occurs on any platform.
- Data is lost after a connection failure or abrupt shutdown.
- Recovery requires manual intervention (e.g., resetting progress).

---

## Notes

- Test on three different devices for each platform (e.g., Android, iOS, standalone VR).
- Simulate low-bandwidth conditions (3G) and high-latency scenarios (200 ms+) for multiplayer testing.