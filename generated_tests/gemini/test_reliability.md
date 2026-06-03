# Test Case - Reliability

**Project:** Educational Metaverse – Battle of Itaparica (Decolonial Perspective)  
**Platform:** Multi-platform (Browser, Mobile, VR Headset) via Spatial.io / Unity  
**Attribute:** Reliability (ISO/IEC 25010)  
**Sub-attributes:** Maturity, Fault Tolerance, and Recoverability  

---

## Objective

Verify the system's **Fault Tolerance** and **Recoverability** by ensuring the metaverse gracefully handles sudden network disconnection during an active student assessment (quiz) and fully restores the exact session state, position, and progress upon reconnection without losing data or crashing.

---

## Steps

1. **Active Session Establishment:** Launch the metaverse on a target device (e.g., a VR headset or mobile browser), log in as a student, and navigate to the Maria Felipa NPC to initiate a historical quiz.
2. **Progress Generation:** Complete 3 out of 5 quiz questions to establish a mid-activity state, verifying that the score data is actively changing.
3. **Network Fault Injection (Disconnect):** While on the 4th question, abruptly disconnect the device's internet connection (toggle Wi-Fi off or disconnect the LAN cable) to simulate sudden network failure. Observe the application's immediate behavior for 60 seconds.
4. **Network Restoration:** Re-enable the internet connection on the device to trigger the system's automatic reconnection protocol.
5. **State Recovery Verification:** Allow the application to re-establish the connection to the Spatial.io cloud servers and verify the integrity of the student's restored environment.

---

## Expected Result

* **Fault Tolerance (Step 3):** The application does not freeze, crash, or display a fatal exception error. It gracefully presents a non-blocking warning message indicating a connection loss while attempting to background-reconnect.
* **Recoverability (Steps 4-5):** Upon network restoration, the system automatically reconnects to the cloud within 5 seconds without requiring a manual application restart. 
* **Data Integrity:** The student avatar is restored to the exact position in front of Maria Felipa, and the quiz resumes precisely at the 4th question with the previous 3 answers perfectly preserved. No progress corruption or duplicate session errors occur.