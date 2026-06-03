# Test Case – Performance Efficiency

## Objective

Verify that the metaverse maintains stable performance across different platforms (web browser, mobile, and VR), with acceptable loading times, smooth frame rates (FPS), and efficient resource utilization.

---

## Steps

1. Initial Loading Test

- Access the metaverse using a web browser (Chrome/Firefox), a mobile device (Android/iOS), and a VR headset (Oculus Quest 2).
- Measure the time from clicking the launch/start button until the 3D environment is fully rendered.

2. Frame Rate (FPS) and Latency Test

- Navigate through the main scenario (Itaparica Island) with 5 active NPCs.
- Use monitoring tools (e.g., Unity Profiler, Chrome DevTools, OVR Metrics Tool) to record:
	- Average FPS (minimum acceptable: 30 FPS on mobile/VR, 60 FPS in browsers).
	- Input latency (movement and object interaction responsiveness).

3. Resource Utilization Test

- Monitor the following metrics for 10 minutes on each platform:
	- CPU/GPU utilization (% usage).
	- RAM consumption (MB/GB).
	- Battery usage (on mobile/VR, percentage consumed per minute).

---

## Expected Result

✅ Initial Loading

- Browser: ≤ 5 seconds.
- Mobile/VR: ≤ 10 seconds.

✅ Frame Rate and Latency

- Stable FPS (≥ 30 on VR/mobile, ≥ 60 in browsers).
- Input latency < 150 ms (imperceptible to the user).

✅ Resource Utilization

CPU/GPU usage does not exceed 70% on recommended devices.
RAM usage remains within acceptable limits (e.g., < 2 GB on mobile, < 4 GB on VR).
Battery drain (mobile/VR) does not exceed 5% per 10 minutes of use.

---

## Failure Criteria

❌ The test fails if:

- Loading time exceeds 15 seconds on any platform.
- FPS drops below 20 on VR/mobile or below 30 in browsers.
- Latency exceeds 200 ms, causing noticeable delays.
- Memory leaks or excessive battery consumption are detected (> 10% battery drain per 10 minutes).

---

## Notes

- Execute the test under different network conditions (4G and 5 GHz Wi-Fi).
- Compare results across low-end devices (e.g., entry-level Android phones) and high-performance devices (e.g., iPhone 15, Oculus Quest 3).