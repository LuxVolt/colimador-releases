# Collimator VCurve — Release history

Manual: [Collimator-VCurve-Manual.pdf](Collimator-VCurve-Manual.pdf)

## v5.6.0 — 2026-08-31

Auditoria de 31/ago (council + Codex + Codex adversarial + pre-mortem do
Martin): FIT nao crasha mais (posicoes repetidas, numero infinito, pasta
read-only, disco cheio); gate de qualidade (vertice fora da varredura ou sem 2 pontos por
lado = invalido); CSV grava o RESULTADO do fit + versao/camera/ROI e nao se
sobrescreve; camera que some nao derruba nem congela o app (religa sozinho)
e resolucao que a camera nao entrega e revertida; camera que muda de
resolucao sozinha e detectada (badge vermelho, PONTO bloqueado); update:
download conferido, troca do .app com rollback, fechar a janela nao corrompe
mais a instalacao, e o update nao interrompe varredura com pontos na
memoria; piso de 1280 valendo p/ camera pequena (teclado/botoes sempre no
canvas); leitura %/rms/max visivel tambem no tablet; log persistente em
~/Documents/colimador/colimador.log + crash log; config.json atomico;
Documents real no Windows com OneDrive; teclas c/q pedem confirmacao como
os botoes.

## v5.5.1 — 2026-08-31

- Fixes the side panel not responding to clicks/taps in v5.5.0 when the
  capture resolution is larger than the on-screen video (e.g. the new
  1080p default on a FullHD monitor) — one boundary check was left on
  the old coordinate space. Found by Martin (mohrlens). If v5.5.0 left
  you stuck: keyboard shortcuts (space, f, ESC) still worked, and this
  update restores the panel.

## v5.5.0 — 2026-08-31

- **Camera resolution is now configurable** in SETTINGS: 720p / **1080p
  (new default)** / MAX (up to 4K). The measurement runs on the full
  chosen resolution — in our synthetic bench study, 1080p roughly
  doubles vertex precision with long lenses and on the 65 mm master.
  Changing it clears the current points (different metric scale), and
  the CSV filename now records the resolution used.
- **Display decoupled from capture**: the live view scales to your
  screen (a FullHD/4K monitor automatically shows more real pixels),
  zoom keeps showing true camera pixels, and a badge at the top right
  shows the actual resolution and frame rate.
- Switching cameras now adopts the new camera's real frame size instead
  of stretching it to the old one.

## v5.4.5 — 2026-08-31

- Fixes the "everything doubled at startup" glitch seen on some Windows
  machines (Intel graphics): the window now opens **already maximized**
  and forces a full repaint, so the compositor can no longer blend the
  old window surface over the new one — which also made buttons hard to
  hit.
- **Single-instance guard**: opening the app twice now shows "already
  running" briefly and closes the extra copy, instead of stacking two
  windows on top of each other.
- The window appears **instantly** with an "opening..." splash while
  cameras are probed — no more silent seconds inviting a second click.

## v5.4.4 — 2026-08-29

- Configurable **max zoom**: 5× (default) or 10×, in SETTINGS next to
  the zoom step. Double-tap and the direct-to-MAX step follow whatever
  ceiling you pick.

## v5.4.3 — 2026-08-29

- Zoom now defaults to smooth **5% steps** per wheel/pinch notch (a
  continuous scroll glides from 1× to 5× in about a second) instead of
  jumping straight to 5×. The 2× step and the direct-to-MAX behaviour
  remain available in SETTINGS, and double-tap still toggles 1× ↔ 5×.

## v5.4.2 — 2026-08-29

- **One-tap silent update**: the update dialog now downloads the new
  version and applies it by itself, then reopens the app — Windows via
  the new installer, macOS by swapping the app from the `.dmg`, Linux by
  replacing the binary in place. If automatic update is not possible
  (offline, `.deb` install, unusual setup) it falls back to opening the
  download page.
- **Proper installers**: Windows now ships as
  `CollimatorVCurve-setup.exe` — install, update or repair by simply
  running it (per-user, no admin needed). Internally the app is an
  unpacked folder, which avoids Windows Defender's `Wacatac.B!ml` false
  positive that hit the v5.4.0 single-file `.exe`. Linux gains a `.deb`
  package with a menu entry (the raw binary is still published). macOS
  keeps the drag-to-Applications `.dmg`.

## v5.4.1 — 2026-08-29

- Readable live readout, bench-multimeter style: the graph still runs at
  video rate, but the numbers now update ~3×/s showing the window
  average — digits hold still between updates. The big number is now
  **% of peak** (the natural readout when hunting a maximum); rms, max
  and the raw value stay as a smaller line with 3 significant digits.

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
