## Deploying A Robot In Different Environments Using Gazebo As The Simulator

Gazebo is an open-source 3D simulation environment that facilitates the creation of realistic scenarios, including the simulation of sensors, robot dynamics, and interaction with objects in a simulated environment. Due to its popularity in the field of robotics, numerous custom worlds are already available. For simulations, we provide diverse environments, including hospitals, warehouses, hawker centers, and campuses. Additionally, we offer a variety of robots such as Jackal, TurtleBot3, Robotino, and more. To simulate the movement of humans, we employ PedSim as dynamic obstacles. Further information can be found in our User Guides section.

**Task Generator Config File**

We create a task generator configuration file to modify various task mode settings.   
This file can be found in the following directory:

```python
/arena-rosnav/arena_bringup/configs/task_generator.yaml
```

| Task Modes  | Settings        | Description      |
|----------   |----------       |----------        |
| random      | static, interactive, dynamic       | The random task mode creates static and dynamic obstacles randomly in the world. <br> In the static settings, inside the task generator config file, you can set the maximum and minimum numbers of randomly spawned static objects. The task generator will then create a random number between the minimum and maximum value. <br> In the dynamic settings, you can set maximum and minimum numbers of randomly spawned dynamic agents. The task generator will then create a random number between the minimum and maximum value. <br>In the random task mode, the robot is assigned a random start and goal position. After the robot reaches the goal, a new start and goal pose will be assigned and new static and dynamic obstacles will be placed randomly in the world. |
| scenario    | scenario_file                      | The random task mode is designed for evaluation in the first place. In the scenario file dynamic and static obstacles as well as the start and goal position of the robot are defined.                                                                              |
| staged      | curriculum, starting_index         | The staged task mode is designed for training processes. In general, it behaves like the random task mode. You can set the number of randomly spawned dynamic and static objects. <br> The difference from the random task mode is that there are multiple stages. In each stage, a different number of dynamic and static objects can be set. If the robot successfully completed the first stage, the next stage will be triggered. <br> The amount of obstacles is defined in a curriculum file. |

#### Worlds

We provide our own worlds:

| <img width="250" height="250" src="../../../tutorials/gazebo_tutorial/images/arena_worlds/arena_hospital_large.png"> | <img width="200" height="200" src="../../../tutorials/gazebo_tutorial/images/arena_worlds/arena_hospital_small.png"> | <img width="240" height="240" src="../../../tutorials/gazebo_tutorial/images/arena_worlds/arena_hawker_centre_1.png"> | 
| :--------------------------------------------------------------: | :---------------------------------------------------------------------: | :--------------------------------------------------------------------: | 
|                           arena_hospital_large                            |                           arena_hospital_small                            |                           arena_hawker_centre                            |            

| <img width="210" height="210" src="../../../tutorials/gazebo_tutorial/images/arena_worlds/COM1_1.png"> | <img width="230" height="230" src="../../../tutorials/gazebo_tutorial/images/arena_worlds/COM2_1.png"> | <img width="200" height="200" src="../../../tutorials/gazebo_tutorial/images/arena_worlds/COM3_1.png"> | 
| :-------------------------------------------------------------: | :---------------------------------------------------------: | :---------------------------------------------------------------: |
|                           arena_nus_com1                           |                     arena_nus_com2                      |                            arena_nus_com3                            |                       

Additionally, we provide many other worlds:

| <img width="400" height="400" src="../../../tutorials/gazebo_tutorial/images/other_worlds/aws_hospital.png"> | <img width="280" height="280" src="../../../tutorials/gazebo_tutorial/images/other_worlds/aws_small_house.png"> |  
| :--------------------------------------------------------------: | :---------------------------------------------------------------------: |  
|                           aws_hospital                            |                           aws_house_small                            |                                      

| <img width="300" height="300" src="../../../tutorials/gazebo_tutorial/images/other_worlds/aws_small_warehouse.png"> | <img width="420" height="420" src="../../../tutorials/gazebo_tutorial/images/other_worlds/factory.png"> |  
| :--------------------------------------------------------------: | :---------------------------------------------------------------------: |  
|                           aws_warehouse_small                            |                           factory                            | 

### Arena Hospital Large

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=arena_hospital_large local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/arena_gifs/./arena_hospital_large.gif)

### Arena Hospital Small

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=arena_hospital_small local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/arena_gifs/./arena_hospital_small.gif)

### AWS Hospital

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=hospital local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/other_worlds_gifs/./aws_hospital_world.gif)

### Arena Hawker Centre

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=arena_hawker_centre local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/arena_gifs/./arena_hawker_centre_1.gif)

### Arena National University Of Singapur COM1 Building

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=arena_nus_com1_building local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/arena_gifs/./arena_nus_com1.gif)

### Arena National University Of Singapur COM2 Building

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=arena_nus_com2_building local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/arena_gifs/./arena_nus_com2.gif)

### Arena National University Of Singapur COM3 Building

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=arena_nus_com3_building local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/arena_gifs/./arena_nus_com3.gif)

### AWS Small House

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=aws_house local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/other_worlds_gifs/./aws_small_house_world.gif)

### AWS Small Warehouse

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=small_warehouse local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/other_worlds_gifs/./aws_small_warehouse_world.gif)

### AWS Factory

```pythom
roslaunch arena_bringup start_arena.launch simulator:=gazebo map_file:=factory local_planner:=teb model:=jackal tm_robots:=random tm_obstacles:=random
```

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/2.0.8/clipboard.min.css">

![](gifs/other_worlds_gifs/./factory.gif)






