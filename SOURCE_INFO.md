# Nav2 1.1.20 source snapshot

This directory contains the Nav2 source archive downloaded on 2026-11-16.

- Upstream: https://github.com/ros-navigation/navigation2
- Tag: `1.1.20`
- ROS 2 distribution: Humble
- Source archive: `navigation2-1.1.20.tar.gz`
- Archive SHA-256: `c965b7a36ef48cd7f35f01c1f98883741693d195dae582232d6d0444d2eedab6`
- Extracted file count: 1389

The upstream `LICENSE`, copyright notices, and source files are preserved.

The `downloads/` directory also contains the files downloaded during the same
Orin environment setup:

```text
downloads/navigation2-1.1.20.tar.gz
downloads/ros.key
downloads/ros-1.key
downloads/ros2-apt-source_1.3.0~jammy_all.deb
```

The two ROS key files are retained because both were downloaded during setup.
They are public signing keys, not private credentials.

To build on Ubuntu 22.04:

```bash
mkdir -p ~/dog_nav_ws/src
mv nav2-1.1.20-repo ~/dog_nav_ws/src/navigation2
cd ~/dog_nav_ws
source /opt/ros/humble/setup.bash
rosdep install --from-paths src --ignore-src -r -y
MAKEFLAGS="-j4" colcon build \
  --symlink-install \
  --executor sequential \
  --packages-up-to nav2_bringup \
  --cmake-args -DCMAKE_BUILD_TYPE=RelWithDebInfo
```
