# Test Case - Compatibility

**Project:** Educational Metaverse – Battle of Itaparica (Decolonial Perspective)  
**Platform:** Multi-platform (Browser, Mobile, VR Headset) via Spatial.io / Unity  
**Attribute:** Compatibility (ISO/IEC 25010)  
**Sub-attribute:** Interoperability & Coexistence  

---

## Objective

Verify multi-platform **Interoperability** and data **Coexistence** by ensuring that a student's session data, quiz progress, and inventory synchronized in real-time on a mobile device immediately reflect when logging into the same account via a VR headset and a desktop web browser without causing performance degradation or data corruption.

---

## Steps

1. **Initial Progress (Mobile):** Open the metaverse on a mobile device (Android/iOS), log in with a test student account, and start the "Battle of Itaparica" experience.
2. **Action & Cloud Save:** Interact with the Maria Felipa NPC, complete the first historical quiz, and collect a specific period inventory item. Confirm that the progress indicators save to the cloud.
3. **Cross-Platform Launch (VR):** Without logging out of the mobile session, put on a VR headset (e.g., Meta Quest), open the Spatial.io application, and log into the exact same student account.
4. **State Verification (VR):** Observe the synchronization of the avatar's location, quiz scores, and historical inventory items within the VR environment.
5. **Simultaneous Verification (Browser):** Open a desktop web browser (e.g., Google Chrome), navigate to the Spatial.io room link, log into the same account, and check if the asynchronous multiplayer state and cloud-saved progress match perfectly across all three active platforms concurrently.

---

## Expected Result

* The metaverse successfully exchanges data across all platforms without synchronization conflicts.
* The student’s quest progression, inventory items, and quiz results are completely accurate and identical across the mobile device, VR headset, and desktop web browser.
* No data loss, account locking, or progress corruption occurs during the simultaneous multi-platform session, and system performance (CPU/GPU) remains stable on all testing devices.