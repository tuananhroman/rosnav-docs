## How to Use Arena Unity
If you want to use Unity Simulator like Gazebo and Flatland, you need the correct integration branch and the Arena Unity build. For this, do the following steps.

### Installing Arena Unity

**Getting the Arena Unity Repo**:  
After installing Arena Rosnav via the manual installation or through the install scripts, execute the following command in *\[catkin_ws\]/src*:
```bash
git clone https://github.com/Arena-Rosnav/arena-unity.git
```

**Getting the Arena Unity Build**:  
To get the executable of the arena unity project execute the corresponding script by running the following command in *\[catkin_ws\]/src/arena-unity* :
```bash
./arena-unity-build.sh 
```

**Getting the Correct Arena Rosnav Branch**:  
All the development on the arena-rosnav repository side has been happening in the unity-simulator branch. To get the branch execute the following command in *\[catkin_ws\]/src/arena-rosnav* :
```bash
git checkout -b unity-simulator origin/unity-simulator
```
The remote respository of the Arena-Rosnav/arena-rosnav repo might not be named origin on your machine. You can check this by running:
```bash
git remote -v
```
After getting the branch, you need to rebuild the workspace using catkin_make.

**Running Arena Unity**:  
You can run Arena Unity simply by executing the normal launch command and specifying Unity as the *simulator*. E.g.:
```bash
roslaunch arena_bringup start_arena.launch simulator:=unity task_mode:=scenario model:=jackal 
```
