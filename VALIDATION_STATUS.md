# Validation Status and Evidence Boundaries

| Claim or artifact | Status | Qualification / next step |
|---|---|---|
| Video decoding and format | Verified | 3,600 frames per camera in evaluated capture |
| Frame hashes and SEI traceability | Reported verified | Based on evaluated record; raw source not included here |
| Stereo frame tick pairing | Verified | 3,600 matching pairs; no missing counter increments |
| Visual frame alignment | Evaluated | Peak global motion correlation at zero-frame lag |
| IMU sample continuity | Verified | Approx. 501.7 Hz; no observed gaps/duplicates/saturation |
| Left/right exposure-center timing | Device-reported | Median 20.5 µs; external optical test still needed |
| Camera–IMU timing offset | Estimated | −1.1/−1.2 ms from image/gyro motion fit; not a final calibration |
| Stereo calibration for 1600 × 1200 mode | **Not validated** | Supplied file appears mode-mismatched; mode-specific calibration needed |
| Camera–IMU extrinsics for evaluated mode | **Not validated** | Mode-specific calibration and verification needed |
| Robot-learning performance improvement | **Not assessed** | No training/benchmark claim |

## Publication scope

These documents and figures describe a **single evaluated recording and configuration**. This public repository contains no raw capture, no executable reproduction pipeline, and no production approval certificate. Do not interpret device-reported values as independently verified ground truth.

Source: [Technical Field Note #03](https://origindatalab.io/technical-field-notes/stereo-imu-egocentric-sample.html).
