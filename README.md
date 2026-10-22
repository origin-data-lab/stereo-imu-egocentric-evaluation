# Stereo + IMU Egocentric Capture — Technical Evaluation

**Origin Data Lab | Technical Field Note #03 | October 2026**

This public repository presents an evidence-oriented evaluation of a **120-second head-mounted stereo egocentric recording with 6-axis IMU**. It documents what was measured, what was inferred, and what remains unverified. It is **not** a production calibration certificate or a release of the raw dataset.

**Technical Field Note:** [English](https://origindatalab.io/technical-field-notes/stereo-imu-egocentric-sample.html) · [한국어](https://origindatalab.io/ko/technical-field-notes/stereo-imu-egocentric-sample.html)

## Capture and key observations

| Item | Reported result | Evidence classification |
|---|---|---|
| Capture | 120 s; stereo 1600 × 1200 at 30 fps | Evaluated capture |
| Frame count | 3,600 frames per camera | Verified |
| Stereo frame ticks | 3,600 / 3,600 pairs matched; 33,333 µs tick interval | Verified from recorded SEI |
| Frame counter continuity | No missing increments in either stream | Verified |
| Visual motion alignment | Maximum correlation at 0-frame lag; r = 0.997 | Evaluated |
| Left–right exposure-center difference | Median 20.5 µs; mean 21.1 ± 2.9 µs | **Device-reported**, not externally verified |
| IMU sample rate | Approximately 501.7 Hz | Verified in evaluated record |
| IMU continuity | No observed duplicates, gaps, or saturation in tested range | Verified in evaluated record |
| Camera–IMU time offset | Left −1.1 ms; right −1.2 ms | **Estimated**, not certified |
| Stereo calibration | Provided calibration parameters do not match the evaluated 1600 × 1200 mode | **Not production-validated** |

## Important limitations

- Sub-millisecond exposure simultaneity has **not** been independently verified with an external optical reference.
- Camera–IMU offsets are **estimates from image motion and gyroscope correlation**, not final production synchronization constants.
- The supplied stereo calibration refers to a different imaging mode. Diagnostic rectification does **not** establish valid production stereo calibration.
- Camera–IMU extrinsic parameters for the evaluated mode have not been validated.
- No claim is made about robot learning performance improvements or generalization across hardware and capture modes.

See [TECHNICAL_REPORT.md](TECHNICAL_REPORT.md) for methods and measurements and [VALIDATION_STATUS.md](VALIDATION_STATUS.md) for claim boundaries.

## Repository contents

- `README.md` — overview and essential limitations
- `TECHNICAL_REPORT.md` — technical methods and results
- `VALIDATION_STATUS.md` — evidence classifications and open validation work
- `figures/` — nine figures reproduced from the published Field Note

**Not included:** raw stereo video, raw IMU files, calibration binaries, device-specific firmware, or independently executable validation scripts. Those should not be inferred from this repository.

## Contact

For evaluation-package availability and project-specific collection: **contact@origindatalab.io** · https://origindatalab.io

© 2026 Origin Data Lab. No license is granted by default for repository content; contact us for reuse permissions.
