# Test Case – Compatibility 

## Objective

Demonstrate that the metaverse:

- Runs alongside common applications (video conferencing, music streaming) without noticeable CPU/GPU or FPS degradation (**Coexistence**).
- Maintains perfectly synchronized progress between the desktop browser, Android app, and Meta Quest 2 (**Interoperability**).

---

## Preconditions

- The same user account is registered and available on all platforms.
- Devices:
    - Windows 11 laptop (RTX 3060) with Chrome 124 and Zoom 6.x.
    - Android 13 smartphone (Snapdragon 865) with the Spatial.io app.
    - Meta Quest 2 (v53) connected to a 5 GHz Wi-Fi network.
- Measurement tools:
    - MSI Afterburner (desktop).
    - Android Studio Profiler.
    - OVR Metrics Tool (Quest).
- Stable 300 Mbps network connection.
- Device battery level ≥ 80%.

---

## Steps

1. On the laptop, start a Zoom meeting with 1080p video enabled and screen sharing active.
2. Open the metaverse in Chrome and join the same multiplayer instance.
3. Explore the environment for 10 minutes while monitoring:
    - FPS.
    - CPU and GPU usage.
    - Zoom call quality (frame rate and latency reports).
4. Complete a minigame and receive a score and a collectible item.
5. Exit the metaverse (without logging out) and close Chrome.
6. On the Android device, open Spotify and play music in the background; then launch the Spatial.io app and log in.
7. Verify that the score, collected item, and avatar position have been synchronized. Play for 5 minutes while recording performance metrics and checking whether Spotify audio experiences interruptions.
8. Send the app to the background, lock the phone for 60 seconds, return to the app, and verify that the state remains intact.
9. On the Meta Quest 2, log in with the same user account and immediately verify that the progress data is correct. Interact with the environment for 5 minutes.
10. Finally, open the progress dashboard in a browser (on any platform) and validate the consistency of the data (score, items, and checkpoints).

---

## Expected Result

|Metric / Behavior|Desktop + Zoom|Android + Spotify|Quest 2|Success Criteria|
|---|---|---|---|---|
|Average FPS|≥ 60|≥ 30|≥ 72|Drop < 20% for ≤ 1 second|
|Average CPU Usage (metaverse)|≤ 65%|≤ 55%|≤ 70%|Peak < 90%|
|Average GPU Usage|≤ 75%|≤ 60%|≤ 80%|Peak < 95%|
|Zoom Latency / Packet Loss|No noticeable increase|N/A|N/A|No "Internet unstable" warning|
|Spotify Audio Interruptions|N/A|0 interruptions > 0.5 s|N/A|—|
|Progress Synchronization|—|< 5 s|< 5 s|Data 100% identical|
|State After Backgrounding (Step 8)|N/A|App resumes at the same location without reloading the entire scene|N/A|—|

---

## Approval Criteria

The test is **approved** if:

- All performance thresholds are met.
- Zoom and Spotify maintain normal quality throughout the test.
- Progress remains intact and identical across all three platforms, with no duplicated or lost items.

The build is **rejected** if:

- Any performance metric exceeds the defined limits.
- Zoom or Spotify quality is negatively affected beyond acceptable thresholds.
- Any synchronization inconsistency, data loss, or data duplication is detected across platforms.