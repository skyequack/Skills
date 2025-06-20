### **get_joint**
**Description:**  
Returns the current joint values (angles or positions) of the robot.

**Parameters:**  
- `robot_to_use` (int, optional): Index or identifier of the robot to query.  
- `wait` (bool, optional): Whether to wait for the latest data.

**Returns:**  
- `list` of joint values (floats).

**Usage Example:**  
```python
joints = get_joint()._run(robot_to_use=1)
```

---

### **get_pose**
**Description:**  
Returns the current pose (position and orientation) of the robot’s end effector (tool center point).

**Parameters:**  
- `robot_to_use` (int, optional): Index or identifier of the robot to query.  
- `wait` (bool, optional): Whether to wait for the latest data.

**Returns:**  
- `list` or `dict` representing the pose (e.g., `[x, y, z, rx, ry, rz]`).

**Usage Example:**  
```python
pose = get_pose()._run(robot_to_use=1)
```

---

### **get_zone_pose**
**Description:**  
Gets the pose of the robot at a named "zone" (predefined position).

**Parameters:**  
- `zone_name` (str): Name of the zone.  
- `robot_to_use` (int, optional): Index or identifier of the robot.  
- `joint_space` (bool, optional): Whether to return joint space or Cartesian space.

**Returns:**  
- `list` or `dict` representing the pose at the specified zone.

**Usage Example:**  
```python
zone_pose = get_zone_pose()._run(zone_name="home", robot_to_use=1)
```

---

### **hand_teach**
**Description:**  
Switches the robot into or out of hand-teach (gravity compensation) mode, allowing manual movement.

**Parameters:**  
- `enable` (bool): True to enable hand-teach mode, False to disable.

**Returns:**  
- `str` status message.

**Usage Example:**  
```python
hand_teach()._run(enable=True)
```

---

### **control_gripper**
**Description:**  
Opens or closes the robot’s gripper. Supports different gripper types (e.g., pneumatic, robotiq).

**Parameters:**  
- `action` (str): "open" or "close".  
- `gripper_type` (str, optional): Type of gripper (e.g., "pneumatic", "robotiq").

**Returns:**  
- `str` status message.

**Usage Example:**  
```python
control_gripper()._run(action="open", gripper_type="robotiq")
```

---

### **delay**
**Description:**  
Adds a time delay (pause) in the script.

**Parameters:**  
- `duration` (float): Time to wait in seconds.

**Returns:**  
- `str` confirmation message.

**Usage Example:**  
```python
delay()._run(duration=2.0)
```

---

### **send_message_to_webapp**
**Description:**  
Sends a message to a web application (e.g., for logging or user notification) via Pusher.

**Parameters:**  
- `message` (str): The message to send.  
- `user` (str, optional): User identifier.

**Returns:**  
- `str` status message.

**Usage Example:**  
```python
send_message_to_webapp()._run(message="Robot started", user="operator1")
```

---

### **move_translate**
**Description:**  
Moves the robot along the x, y, z axes by a specified amount from its current position.

**Parameters:**  
- `dx` (float): Translation along x-axis.  
- `dy` (float): Translation along y-axis.  
- `dz` (float): Translation along z-axis.  
- `robot_to_use` (int, optional): Index or identifier of the robot.

**Returns:**  
- `str` status message.

**Usage Example:**  
```python
move_translate()._run(dx=0.1, dy=0.0, dz=0.0, robot_to_use=1)
```

---

### **move_to_joint**
**Description:**  
Moves the robot to a specific joint configuration or a named pose.

**Parameters:**  
- `joint_values` (list of float): Target joint angles.  
- `pose_name` (str, optional): Name of a predefined pose.  
- `robot_to_use` (int, optional): Index or identifier of the robot.

**Returns:**  
- `str` status message.

**Usage Example:**  
```python
move_to_joint()._run(joint_values=[0, 1.57, 0, 0, 0, 0], robot_to_use=1)
```

---

### **move_to_pose**
**Description:**  
Moves the robot to a specific Cartesian pose (position and orientation).

**Parameters:**  
- `pose` (list or dict): Target pose (e.g., `[x, y, z, rx, ry, rz]`).  
- `robot_to_use` (int, optional): Index or identifier of the robot.

**Returns:**  
- `str` status message.

**Usage Example:**  
```python
move_to_pose()._run(pose=[0.5, 0.0, 0.3, 0, 3.14, 0], robot_to_use=1)
```

---

### **move_in_trajectory**
**Description:**  
Moves the robot through a series of waypoints (trajectory).

**Parameters:**  
- `waypoints` (list of poses): List of poses to follow.  
- `robot_to_use` (int, optional): Index or identifier of the robot.

**Returns:**  
- `str` status message.

**Usage Example:**  
```python
move_in_trajectory()._run(waypoints=[[...], [...], [...]], robot_to_use=1)
```

---

### **save_pose**
**Description:**  
Saves the current pose of the robot to a JSON file for later use.

**Parameters:**  
- `pose_name` (str): Name to save the pose under.  
- `robot_to_use` (int, optional): Index or identifier of the robot.

**Returns:**  
- `str` status message.

**Usage Example:**  
```python
save_pose()._run(pose_name="inspection_point", robot_to_use=1)
```

---

### **save_joint_angles**
**Description:**  
Saves the current joint angles of the robot to a JSON file for later use.

**Parameters:**  
- `joint_name` (str): Name to save the joint configuration under.  
- `robot_to_use` (int, optional): Index or identifier of the robot.

**Returns:**  
- `str` status message.

**Usage Example:**  
```python
save_joint_angles()._run(joint_name="home_position", robot_to_use=1)
```

---
