^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package av_car_meshes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Forthcoming
-----------

3.1.0 (2026-02-24)
------------------

3.0.0 (2025-08-11)
------------------
* Update camera and lidar TFs based on new calibration (`#35 <https://github.com/ipab-rad/av_car_description/issues/35>`_)
  - Use `lidar_top` instead of `lidar_ouster_top`
  - Add new `lidar_front_mount` -> `lidar_front` TF
  - Transformations updated:
  - `vehicle_roof_datum` -> `lidar_X_mount`
  - `lidar_X_mount` -> `lidar_X`
  -  `camera_X_sensor` -> `camera_X_optical`
* Contributors: Hector Cruz

2.0.0 (2024-11-11)
------------------
* Add *_mount and *_sensor chains for IMUs/GPS
  - Define `imu_rear_mount` -> `imu_rear_sensor` and
  `imu_fps_r_mount` -> `imu_fps_r_sensor` TFs
  - `*_mount` frames describe the physical sensor
  orientation
  - `*_sensor` frames describe the orientation that is
  consistent with the microstrain IMU ROS driver ENU measurements
  - Fix `imu_rear_mount` Y translation based on in-house
  measurements
  - Fix `gps_antenna\_*_mount` translation based on in-house
  measurements
  - Define `gps_antenna\_*_mount` -> `gps_antenna\_*_sensor` TF
    based on GNSS antenna hight relative to mount
* Remove `oxts*` frames and parameters as the sensor is no longer
  mounted in the vehicle
  
* Contributors: Hector Cruz

1.6.0 (2024-10-18)
------------------
* Refactor LIDAR mounting structure based on LIDAR calibration.
  - Perform adjustments based on calibration between `lidar_ouster_top` and both `lidar_left`
    and `lidar_right`.
    - Update the old chain: `vehicle_roof_datum -> lidar_left` and 
      `vehicle_roof_datum -> lidar_right` to:
      - `vehicle_roof_datum -> lidar_left_mount -> lidar_left`
      - `vehicle_roof_datum -> lidar_right_mount -> lidar_right`
  - Ensure that the new chain `vehicle_roof_datum -> lidar_x_mount` matches 
    the old `vehicle_roof_datum -> lidar_x` TF for future reference.
* Contributors: Hector Cruz, hect95

1.5.1 (2024-10-07)
------------------
* Update fsp_l camera tf (`#17 <https://github.com/ipab-rad/av_car_description/issues/17>`_)
* Contributors: Hector Cruz

1.5.0 (2024-09-24)
------------------
* New camera extrinsics (`#16 <https://github.com/ipab-rad/av_car_description/issues/16>`_)
  - Update camera extrinsics based on camera lidar calibration
  - The extrinsics are based on camera configuration defined in
  https://github.com/ipab-rad/av_camera/pull/7
* Contributors: Hector Cruz

1.4.0 (2024-09-04)
------------------
* Update `robot_state_publisher` package to the `ipab-rad` version to 
  continuously publish `tf_static` topic

* Contributors: hect95

1.3.0 (2024-06-24)
------------------
* Prepend all sensor/optical frames with `camera\_`
* Add sensor and optical frames for all cameras
  - Sensor frame is a rotation of mount but in camera coordinates
  - Optical frame TF values now 0s will change in future when sensors are
    calibrated with each other (i.e. cross-sensor registration)
* Contributors: Alejandro Bordallo

1.2.0 (2024-06-05)
------------------
* Add bash args to optionally load local cyclone_dds
* Contributors: Alejandro Bordallo, hect95

1.1.0 (2024-05-21)
------------------
* Add Cyclone DDS ROS RMW and configure for high msg throughput
* Avoid overriding dev and runtime images when using docker scripts
* Allow colorised ROS log

1.0.1 (2024-04-30)
------------------
* Fix pkg names (`#3 <https://github.com/ipab-rad/av_car_description/issues/3>`_)
  This PR adds `av\_` prefix and correct all the references that contian
  `car_description` into `av_car_description`
* Contributors: Hector Cruz

1.0.0 (2024-04-26)
------------------
* Fix pre-commit linting, advice and suggestions
* Fix pkg names, vers. and descriptions pre-release
* Add Hector Cruz as maintainer
* Updating mondeo mesh to match Univeristy vehicle colors
* Updating car meshes to match university colors and avoid errors in RVIZ
  - mondeo_blue.dae is modified to points to a new grey color scheme png images
  - mondeo_blue_body.png is deleted
* Changing CMakeLists installation to align with ROS2 convention rather than using catkin macros
* Add pre-commit config file and run it on repo
* Port original pkg to ROS2
* Contributors: Alejandro Bordallo, hect95
