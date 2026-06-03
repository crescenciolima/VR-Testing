# Test Case - Performance Efficiency

**Project:** Educational Metaverse – Battle of Itaparica (Decolonial Perspective)  
**Platform:** Mobile Devices (via Browser or Spatial.io App)  
**Attribute:** Performance Efficiency (ISO/IEC 25010)  
**Sub-attributes:** Time Behavior & Resource Utilization  

---

### Objective

Validate that the metaverse maintains an acceptable frame rate (FPS), low input latency, stable loading times, and sustainable resource utilization (CPU, GPU, RAM, and battery) on a mobile device during an active multiplayer session with high-density 3D assets.

---

### Steps

1. **Profiler Connection:** Connect a target mobile test device to a profiling tool (e.g., Unity Profiler, Android Studio Profiler, or Xcode Instruments) and launch the "Battle of Itaparica" metaverse room.
2. **Load Time Measurement:** Record the initial room loading time from the moment the URL/room link is executed until the 3D environment, including the island assets and Maria Felipa NPC, is fully rendered and interactive.
3. **Stress & Latency Testing:** Navigate the student avatar through high-density graphical areas (e.g., areas with multiple buildings, historical objects, and asynchronous multiplayer avatars interacting at the same time). Run, jump, and trigger a minigame to measure input latency.
4. **Metric Logging:** Monitor and log the device’s performance metrics continuously for 15 minutes of uninterrupted gameplay, specifically tracking Frame Rate (FPS), CPU utilization, GPU load, and Memory (RAM) footprint.
5. **Thermal & Battery Check:** Check the device's battery level and temperature before starting the test and immediately after the 15-minute mark to assess battery consumption rate and thermal throttling impacts.

---

### Expected Result

* **Time Behavior:** 
    * The initial room loading time does not exceed 10 seconds on a standard high-speed connection. 
    * The frame rate remains stable at a minimum of 30 FPS (ideally 60 FPS on supported mobile devices) with no noticeable stuttering or spikes. 
    * Input latency remains imperceptible (under 100ms) during avatar movement and minigame interaction.
* **Resource Utilization:** 
    * CPU and GPU utilization do not max out at 100% consistently, maintaining an average below 85% to avoid aggressive thermal throttling. 
    * Memory usage remains stable without leaks, staying well within the device's operational limits. 
    * Battery consumption does not drop by more than 4% during the 15-minute test window, and the device does not exhibit excessive overheating.