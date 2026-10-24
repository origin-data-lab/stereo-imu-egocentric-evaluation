# Validation Status and Evidence Boundaries

| Claim or artifact | Status | Qualification / next step |
|---|---|---|
| Video decoding and format | Verified | 3,600 frames per camera in evaluated capture |
| Frame hashes and SEI traceability | Reported verified | Based on evaluated record; raw source not included here |
| Stereo frame tick pairing | Verified | 3,600 matching pairs; no missing counter increments |
| Visual frame alignment | Evaluated | Peak global motion correlation at zero-frame lag |
| IMU sample continuity | Verified | Approx. 501.7 Hz; no observed gaps/duplicates/saturation |
| Left/right exposure-center timing | Device-reported | Median 20.5 µs; external optical test still needed |
| Camera–IMU timing offset | Estimated | −1.1/−1.2 ms from image/gyro motion fit; supports alignment within a few milliseconds only (see update below) |
| Stereo calibration for 1600 × 1200 mode | **Verified (update)** | Mode-matched Kalibr calibration validated on this recording: median angular epipolar error 0.41 px ([Field Note #04](https://origindatalab.io/technical-field-notes/stereo-calibration-check.html)) |
| Camera–IMU extrinsics for evaluated mode | **Calibrated, not independently verified** | Kalibr values exist; natural motion in this recording cannot verify them to the millisecond |
| Robot-learning performance improvement | **Not assessed** | No training/benchmark claim |

## Update — 23 October 2026

- A Kalibr calibration produced in the same 1600 × 1200 capture mode was validated on this recording without adjustment: median angular epipolar error **0.41 px**, stereo-rotation correction below **0.02°**. Details: [Technical Field Note #04](https://origindatalab.io/technical-field-notes/stereo-calibration-check.html).
- The same target-free video–gyro method, applied to a recording with a Kalibr camera–IMU reference, missed the reference time shift by several milliseconds. The −1.1 / −1.2 ms estimate should be read as consistency within a few milliseconds, not as a measured offset.

## Publication scope

These documents and figures describe a **single evaluated recording and configuration**. This public repository contains no raw capture, no executable reproduction pipeline, and no production approval certificate. Do not interpret device-reported values as independently verified ground truth.

Source: [Technical Field Note #03](https://origindatalab.io/technical-field-notes/stereo-imu-egocentric-sample.html).
