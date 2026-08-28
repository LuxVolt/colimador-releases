# Collimator VCurve — Release history

Manual: [Collimator-VCurve-Manual.pdf](Collimator-VCurve-Manual.pdf)

## v5.4.0 — 2026-08-28

**New**

- **SETTINGS** button (replaces DRIVER, which now lives inside it on
  Windows): configurable **photos & CSV folder** (with an OPEN shortcut),
  zoom step, and gesture switches.
- **View zoom** centered on the ROI (display only — the measurement always
  uses the raw image): pinch / Ctrl+wheel, on-screen **− / +** buttons,
  `+`/`-` keys, and **double-tap** jumps straight to 5×.
- **Peak hold** on the focus graph (dashed line + max) and an **RMS**
  readout next to the raw metric.
- The micrometer pad opens with the **previous value pre-selected** —
  just type to replace it.
- **?** menu: **SEND REPORT** (in-app message box, delivered straight to
  support), **CHECK FOR UPDATE** and **MANUAL**.
- The app checks for new versions at startup and asks before opening the
  download page.

**Fixed**

- The **± uncertainty** of the FIT was inflated when micrometer readings
  were far from zero (a covariance term was dropped). The vertex itself
  was always correct; only the reported ± changes.
- A dropped camera frame during POINT no longer biases the metric low.
- Unplugging the camera no longer freezes the app.
- A stray tap on the image no longer resets the ROI.

## v5.3.2 — 2026-08-07

- Maximized window with no black bars on any screen shape; large
  sparkline strip under the video.
- CLOSE and **?** (help) buttons in the side panel.

## v5.3.0 — 2026-08-04

- **Mirror tilt** measured during the scan and reported with FIT results
  (the image centroid traces a spiral as the micrometer spindle turns).
- CSV gains the centroid columns `cx_px, cy_px`.

## v5.2.0 — 2026-07

- App renamed **Collimator VCurve**.
- Camera selector with a **live thumbnail** per input; last camera
  remembered.
- Keypad: negative sign and **mm | µm** input toggle (persisted).
- First PDF manual.

## v5.1.1 — 2026-07-17

- macOS: camera permission fixed in the `.dmg` build (the app looked like
  it would not open).

## v5.1.0 — 2026-07-16

- PT/EN language toggle; window opens maximized.
- First builds for the three platforms (Windows / macOS / Linux).
