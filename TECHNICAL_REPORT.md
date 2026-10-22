# Technical Report — Stereo + IMU Egocentric Capture

**Technical Field Note #03 · Origin Data Lab · October 2026**

This document summarizes the published evaluation; it is not an independent reanalysis of the underlying raw capture. Refer to the [English Field Note](https://origindatalab.io/technical-field-notes/stereo-imu-egocentric-sample.html) for the public-facing narrative and illustrations.

## 1. Evaluated recording

A 120-second indoor workbench task involving two-handed case assembly with a powered drill and hand tools was captured with a head-mounted stereo camera and six-axis IMU. Left and right streams were each **1600 × 1200, 30 fps, 3,600 frames**. Camera frame ticks, exposure starts and exposure durations were recorded in H.264 SEI metadata.

## 2. Frame timing and stereo correspondence

A camera integrates light over an exposure interval. The analysis uses **exposure-center time = exposure-start time + 0.5 × exposure duration**, rather than assuming the MP4 presentation timestamp is the hardware exposure timestamp. Exposure durations varied approximately **8.1–12.0 ms**.

- Recorded stereo ticks agreed for **3,600 / 3,600 frame pairs**, at **33,333 µs** intervals.
- Strobe counters increased by one frame with **zero observed missing increments**.
- Global visual motion correlation peaked at **0-frame lag (r = 0.997)**.
- Device-reported left/right exposure-center difference: **median 20.5 µs**, **mean 21.1 ± 2.9 µs**; reported p1–p99 **16.5–31.0 µs**.

The microsecond-scale timing is **device-reported**, not externally validated. A simultaneous LED-flash test visible to both cameras is one potential independent validation method.

## 3. IMU stream

The six-axis IMU averaged approximately **501.7 Hz**. In the evaluated range, no sample-spacing outliers, duplicates, gaps or sensor saturation were observed. The IMU record extended about **48 ms before the first video exposure** and **48 ms after the last exposure**. The mean acceleration magnitude reported in the figure is **9.893 m/s²**.

## 4. Camera–IMU offset estimation

The evaluation compared image-derived head motion with gyroscope data:

1. Estimate interframe image motion at **400 × 300** using Lucas–Kanade optical flow and a RANSAC similarity transform.
2. Average gyroscope signals between exposure centers.
3. Fit a **3 × 3 linear map plus bias** by least squares.
4. Search offsets from **−6 to +6 ms** in **0.1 ms** increments and assess stability across six 30-second windows.

| Metric | Left camera | Right camera |
|---|---:|---:|
| Best-fit full-sequence offset | −1.1 ms | −1.2 ms |
| Fit R² | 0.973 | 0.974 |
| 30-second window range | −1.5 to −0.7 ms | −1.5 to −0.8 ms |

The per-axis R² values reported in the comparison figure are **0.971 / 0.972 / 0.979**. A manufacturer calibration from a **different sensor mode** reported **+0.89 / +0.95 ms**; this discrepancy remains unresolved. These values must **not** be treated as final camera–IMU synchronization constants.

## 5. Stereo calibration limitation

A supplied calibration file reported stereo RMS **0.362 px**, but its principal point appeared consistent with **1920 × 1080 (16:9)** while the evaluated capture was **1600 × 1200 (4:3)**. Applying that file produced systematic position-dependent vertical residuals.

A diagnostic three-degree-of-freedom rotation adjustment reduced the holdout median vertical residual to **0.570 px**, but involved approximately **−1.41°** of yaw and shifted right-image points horizontally by approximately **−20.9 px**. This diagnostic adjustment is **not** an approved production rectification or calibration.

## 6. Conclusions and boundaries

Frame-level correspondence, recorded timestamp consistency and IMU continuity were supported for this capture. Microsecond exposure timing remains device-reported, camera–IMU timing is estimated, and mode-matched stereo calibration and extrinsic validation remain open.

This report makes no claim of independent microsecond-level synchronization validation, production calibration acceptance, cross-mode reproducibility, or improvement in robot-learning outcomes.
