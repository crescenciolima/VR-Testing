# Test Case – Performance

## Objective

Evaluate whether the metaverse maintains:

* Stable FPS, acceptable input latency, and fast loading times (**Time Behavior**).
* CPU, GPU, RAM, and battery consumption within safe limits on desktop, mobile (Android), and VR (Quest 2) devices (**Resource Utilization**).

---

## Preconditions

* Production build deployed on Spatial.io with logging enabled (Unity Remote Profiler + WebRTC Stats plugin).
* Dummy accounts (10) available for an asynchronous multiplayer session.
* Measurement tools:

  * Gaming PC (RTX 3060 / 16 GB RAM / Chrome) with MSI Afterburner.
  * Android smartphone (Snapdragon 865 / 8 GB RAM) with Android Studio Profiler and Battery Historian.
  * Meta Quest 2 (v53) with OVR Metrics Tool.
* 5 GHz Wi-Fi network, 300 Mbps bandwidth, and latency below 20 ms to the server.
* Browser cache cleared before each test run.

---

## Steps

### 1. User Synchronization

* Log in 10 bot accounts and 1 human tester into the same instance.
* Keep the bots idle to simulate player presence.

### 2. Loading Test

a. Start a timer and access the metaverse URL.

b. Record:

* **Time to First Frame (TTFF)**.
* **Time to Interact (TTI)** (the moment the avatar can move).

### 3. Intensive Exploration (3 Minutes)

a. Explore the island using both teleportation and continuous locomotion.

b. Interact with the NPC Maria Felipa and accept the first minigame.

c. During the minigame:

* Generate 30 rapid inputs (jumps, clicks, movements).
* Record average input latency using timestamp comparisons between input events and visual responses.

### 4. Metrics Collection (Run in Parallel)

Monitor and record:

* Minimum, average, and maximum FPS.
* Average and peak CPU utilization (%).
* Average and peak GPU utilization (%).
* RAM usage (MB).
* Battery consumption during 10 minutes of gameplay on mobile and VR devices.

### 5. Repeat Testing

Repeat Steps 2–4 on:

* Desktop PC.
* Android device.
* Standalone Quest 2 headset.

### 6. Data Export

Export:

* Performance logs.
* Metric screenshots.
* Gameplay recordings.

Store the collected artifacts for analysis.

---

## Expected Result

| Metric                     | Desktop | Android  | Quest 2 | Approval Criteria                                   |
| -------------------------- | ------- | -------- | ------- | --------------------------------------------------- |
| Average FPS                | ≥ 60    | ≥ 30     | ≥ 72    | No drops below 80% of target for more than 1 second |
| Input Latency              | ≤ 80 ms | ≤ 120 ms | ≤ 70 ms | Measured during Step 3c                             |
| TTFF (Time to First Frame) | ≤ 5 s   | ≤ 7 s    | ≤ 6 s   | At 300 Mbps                                         |
| Time to Interact           | ≤ 10 s  | ≤ 12 s   | ≤ 10 s  | —                                                   |
| Average CPU Usage          | ≤ 70%   | ≤ 65%    | ≤ 75%   | Peak < 90%                                          |
| Average GPU Usage          | ≤ 80%   | ≤ 70%    | ≤ 85%   | Peak < 95%                                          |
| RAM Usage                  | ≤ 3 GB  | ≤ 1.5 GB | ≤ 2 GB  | No memory leaks (>5% growth after 10 min)           |
| Battery Drain (10 min)     | N/A     | ≤ 6%     | ≤ 8%    | —                                                   |

---

## Approval Criteria

The test is **approved** if **all** metrics remain within the specified limits across all three platforms.

The build is **rejected** if any metric exceeds its threshold or if significant performance degradation is observed.

---

## Suggested Next Steps

### Stress Testing

* Execute a stress test with 50 concurrent players to evaluate large-scale rendering and multiplayer performance limits.

### Network Resilience Testing

* Test on a 4G connection with 3% packet loss to evaluate quality adaptation and network resilience.

### FPS Heat Map Analysis

* Generate FPS heat maps to identify particularly demanding 3D areas and optimize:

  * Level of Detail (LOD) configurations.
  * Object occlusion and culling strategies.
  * Asset streaming behavior.
