# URJC Building World ROS package

The simulation enviroment is based on URJC Fuenlabrada Campus, where it is located this building. This world could be used to create new algorithms in localization or navigation. 

![Gazebo01](docs/images/img_1.png)
![Gazebo02](docs/images/img_2.png)
![Gazebo00](docs/images/img_0.png)


# Include the world from another package

<!-- * Update .rosinstall to clone this repository and run `rosws update` -->
<!-- ```
- git: {local-name: src/urjc-excavation-world, uri: 'https://github.com/juanscelyg/urjc-excavation-world.git', version: main}
``` -->
* Add the following to your launch file:
```python
    urjc_building = launch.actions.IncludeLaunchDescription(
        launch.launch_description_sources.PythonLaunchDescriptionSource(
            os.path.join(
                get_package_share_directory('urjc_building_3_world'),
                'launch',
                'urjc_building_3_1st.launch.py')))
```

# Load directly into Gazebo (without ROS)
```bash
export GAZEBO_MODEL_PATH=`pwd`/models
gz sim worlds/urjc_building_3_1st.world
```

# ROS Launch with Gazebo viewer (without a robot)
```bash
# build for ROS
source /opt/ros/jazzy/setup.bash
source /usr/share/gazebo/setup.sh
rosdep install --from-paths . --ignore-src -r -y
colcon build

# run in ROS
source install/setup.sh
ros2 launch urjc_building_3_world urjc_building_3_1st.launch.py
```
# Lights and Shadow configuration

For to obtain a better performance the shadows were disabled. If you want to enable them, you can do it in the file `urjc_building_3_1st.world`, modifying the line:

```xml
<cast_shadows>0</cast_shadows>
```
to

```xml
<cast_shadows>1</cast_shadows>
```

<!-- # Building
Include this as a .rosinstall dependency in your SampleApplication simulation workspace. `colcon build` will build this repository.

To build it outside an application, note there is no robot workspace. It is a simulation workspace only.

```bash
rosws update
rosdep install --from-paths . --ignore-src -r -y
colcon build
``` -->
