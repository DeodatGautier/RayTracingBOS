# Ray Tracing BOS

**Ray tracing and refractive-index fitting for Background-Oriented Schlieren (BOS) experiments.**

Simulate light propagation through a refractive-index field and a thin lens, inspect sensor displacements, and fit a parameterized profile to experimental data.

This repository provides application downloads and documentation. Application source code is not published.

[**Download the latest Windows release**](https://github.com/DeodatGautier/RayTracingBOS/releases/latest) · [Report a problem](https://github.com/DeodatGautier/RayTracingBOS/issues)

## Download and install

1. Open the latest release and expand **Assets**.
2. Download `RayTracingBOS-Setup-1.0.0-x64.exe`.
3. Run the installer and launch **Ray Tracing BOS** from the Start menu.

Windows 10/11, x64. Python is not required. Installation is per user; the installer offers English and Russian. The application interface uses English labels. A desktop shortcut is optional.

GitHub's automatically generated “Source code” archives are not application installers.

## Features

- RK4 ray tracing through Gaussian, Lorentzian, smoothed-step, parabolic and linear-X refractive-index profiles.
- Thin-lens geometry with parallel, central-ray and full-aperture beam modes.
- Trajectory, refractive-index and sensor-displacement visualization.
- Experimental data import from Excel (`.xlsx`, `.xls`), CSV and text files.
- Bounded parameter fitting with fixed-parameter controls and live optimization history.
- Comparison plots, numerical result export, plot saving and reusable JSON presets.

## Quick start

1. Select a refractive-index profile and its parameters.
2. Set the screen size, focal length and object-to-screen/lens distances in **Optical Setup** (all in mm).
3. Click **Run Simulation (F5)** and inspect **Trajectories** and **Analysis**.
4. Load experimental data using **Load Experimental Data (Ctrl+O)**.
5. Set fixed parameters and bounds with **Fix Bounds...**, then click **Run Optimization (F6)**.
6. Inspect **Optimization** and **Comparison**, and export the results.

The demonstration geometry uses a 10 mm screen, 50 mm focal length, 50 mm object-to-screen and object-to-lens distances, and 1000 rays. It gives a thin-lens image magnification of -1 (equal size, inverted). Set the actual geometry of your experiment before fitting measurements.

## Experimental data and interpretation

The first two columns are interpreted as position `x` and displacement `delta`, both in millimetres. Excel import uses the first sheet. At least three distinct finite positions are required; repeated positions are averaged.

For comparison, position is the ideal image position with reversed physical sensor-axis direction: `comparison_x = -sensor_x_ideal`. Displacement is `sensor_x - sensor_x_ideal`. Calibrate your experimental origin, axis direction and pixel-to-mm scale accordingly. Displacement is already a sensor-plane quantity; do not apply magnification a second time.

The fitted objective is displacement mean squared error (MSE, mm²). A small residual alone does not prove a unique refractive-index profile or validate the physical model. Radial profiles assume axial symmetry; the linear-X profile is a separate transverse-gradient model. The application does not directly reconstruct temperature or density.

## Settings and updates

Use **Settings (Ctrl+,)** for beam and numerical options and JSON presets to retain configurations. User presets and logs are stored under `%LOCALAPPDATA%\Nanolab\RayTracingBOS` and are preserved on uninstall. Close the application before installing an update.

## Verify a download

Download the matching `.sha256` asset and compare it with the output of:

```powershell
Get-FileHash -Algorithm SHA256 .\RayTracingBOS-Setup-1.0.0-x64.exe
```

A matching checksum confirms file integrity; it is not a digital signature.

## Authors

Alexander Kurilov · Peter Krasnov

## Related software

[SchlierenEye](https://github.com/DeodatGautier/SchlierenEye) provides BOS displacement analysis of image pairs and videos. Ray Tracing BOS provides the separate ray-tracing and parameter-fitting workflow.

## Reporting problems

Open an issue with the application version, Windows version, reproduction steps, geometry, profile and expected/actual behavior. Include a small input sample or screenshot where useful, after removing private information.
