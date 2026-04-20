# Robotics Workbench

This repository contains a 2D localization workflow based on ICP (Iterative Closest Point), using:
- robot odometry,
- LiDAR scans,
- occupancy-grid map snapshots.

The main implementation currently lives in the notebook [`icp.ipynb`](icp.ipynb), and generated pose estimates are stored in [`icp_results.csv`](icp_results.csv).

## Repository Layout

```text
.
├── icp.ipynb
├── icp_results.csv
├── point_to_plane_icp.py
├── output_all_contours.png
└── files
    ├── map_info.csv
    ├── map_obstacles.csv
    ├── odom.csv
    ├── scan.csv
    ├── tf.csv
    └── map_images/
```

## Data Files

- `files/odom.csv`: odometry trajectory (`x`, `y`, `yaw`, velocities) indexed by nanosecond timestamp (`t_ns`).
- `files/scan.csv`: LiDAR scans (`angle_min`, `angle_inc`, range columns `r0...r359`) indexed by `t_ns`.
- `files/map_info.csv`: metadata for each map image (resolution, size, world origin).
- `files/map_images/*.png`: occupancy grid snapshots.
- `files/map_obstacles.csv`: precomputed obstacle points in world coordinates.
- `files/tf.csv`: frame transforms between robot/map frames.
- `icp_results.csv`: per-step ICP pose estimate and error metrics.

## Setup

Create and activate a Python virtual environment:

```bash
python3 -m venv env
source env/bin/activate
```

Install dependencies used by the notebook:

```bash
pip install numpy pandas matplotlib scipy opencv-python jupyter
```

## Run

Launch Jupyter and open the notebook:

```bash
jupyter lab icp.ipynb
```

If JupyterLab is not installed, use:

```bash
jupyter notebook icp.ipynb
```

## Notes

- `point_to_plane_icp.py` is currently empty; the active pipeline is in the notebook.
- The repository includes large CSV artifacts, especially `files/map_obstacles.csv`.
