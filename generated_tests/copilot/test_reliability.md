# Test Case – Reliability

## Objective

Demonstrate that the metaverse:

* Does not experience critical failures during 15 minutes of normal use (**Maturity**).
* Maintains operation or recovers transparently after a complete network connection loss (**Fault Tolerance**).
* Restores the saved state within 45 seconds, without progress loss or data corruption, after reconnection or a forced client restart (**Recoverability**).

---

## Preconditions

* Production build published on Spatial.io, with autosave enabled after every significant event (checkpoint, dialogue completion, or quiz response).
* Fresh student account (0% progress).
* Desktop environment:

  * Chrome 124.
  * 300 Mbps Wi-Fi connection (controllable access point).
* Tools:

  * Charles Proxy for network interruption simulation.
  * ChromeCrash extension for forcing browser tab crashes.
* Unity Logger configured to export event IDs and timestamps to Kibana.

---

## Steps

1. Access the metaverse, create an avatar, and begin free exploration.

2. For 15 minutes, perform the following cycle:

   * Explore the island.
   * Talk to Maria Felipa.
   * Complete one short quiz.
   * Collect three artifacts.

   Record any errors, visual glitches, or unexpected client crashes.

3. During a second quiz (question 2 of 5), completely disconnect the Wi-Fi network for 60 seconds.

   Observe how the interface responds:

   * Reconnection message.
   * Pause behavior.
   * Freezing.
   * Single-player fallback mode.

4. Re-enable the Wi-Fi connection and measure the time until:

   a. The reconnection is detected.

   b. The player regains control at the same point or at the latest autosave checkpoint.

   c. The interface displays a **"Progress synchronized"** confirmation message.

5. Without logging out, force a browser tab crash using ChromeCrash.

6. Reopen the browser, log in again, and load the session.

   Verify that:

   * The quiz resumes at question 2 of 5 or advances correctly.
   * Previously collected artifacts are still present.
   * The avatar's location matches the most recent checkpoint.

7. Export client logs and compare them with server-side events to detect any state discrepancies.

---

## Expected Result

### Step 2 – Maturity

* Zero crashes or critical failures.
* No more than one minor visual glitch.
* Stable CPU and memory usage.
* No unhandled exceptions recorded in the logs.

### Step 3 – Fault Tolerance

* The game displays a **"Connection Lost"** warning within 5 seconds.
* The quiz timer is paused (or a safe offline mode is enabled).
* No fatal errors occur.

### Step 4 – Reconnection

* Full reconnection is completed within 30 seconds.
* Maximum progress loss is limited to 30 seconds.
* Player position, score, and inventory remain intact.

### Step 6 – Recoverability

* The session is restored within 45 seconds.
* The restored state is identical to the state at the end of Step 4.
* Artifact count and quiz responses are correct.
* No duplicate items are created.

### Logging Validation

* Client and server logs match 100% (identical data hashes).
* The `autosave_ok` tag is recorded before and after each failure event.

---

## Approval Criteria

The test is **approved** if all criteria above are satisfied.

The build is **rejected** if any of the following occur:

* A critical failure or crash.
* Progress loss exceeding 30 seconds.
* Any discrepancy between client and server state.
* Data corruption, duplication, or incomplete recovery.