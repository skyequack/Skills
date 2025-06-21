# Base Skills

## [**Robot State and Movement**](https://github.com/skyequack/Skills?tab=readme-ov-file#robot-state-and-movement-1)

- **get_joint**: Returns current joint values of a robot.
- **get_pose**: Returns the current pose (position) of the robot’s end effector.
- **get_zone_pose**: Gets the pose of the robot at a named "zone" (predefined position).
- **hand_teach**: Switches the robot into/out of hand-teach (gravity) mode.
- **control_gripper**: Opens/closes the robot’s gripper (supports pneumatic and robotiq models).
- **delay**: Adds a time delay in the script.
- **send_message_to_webapp**: Sends a message to a web application via Pusher.
- **move_translate**: Moves the robot along x, y, z axes by a specified amount.
- **move_to_joint**: Moves the robot to a specific joint configuration or named pose.
- **move_to_pose**: Moves the robot to a specific pose (cartesian position).
- **move_in_trajectory**: Moves the robot through a series of waypoints (trajectory).
- **save_pose**: Saves the current pose of the robot to a JSON file.
- **save_joint_angles**: Saves the current joint angles to a JSON file.
## **[Object and Vision Skills](https://github.com/skyequack/Skills?tab=readme-ov-file#object-and-vision-skills-1)**

- **get_best_match**: Finds the best-matching object name from a list using string similarity.
- **get_object_list**: Returns the list of detectable objects.
- **check_pose**: Gets the position of an object in the robot’s workspace using vision.
- **analyze_camera_frame**: Analyzes the camera feed with a prompt (can perform OCR).
- **set_context_camera**: Sets which camera is used for context or detection.
- **compare_images**: Compares two images and returns the difference based on a prompt.
## **[Utility Skills](https://github.com/skyequack/Skills?tab=readme-ov-file#utility-skills-1)**

- **industry_test**: Moves the robot through a list of poses for a number of cycles (for testing).
- **recording_object**: Moves the robot through a set of named poses, then returns home.
- **custom_tour**: Runs a custom tour (sequence of actions) based on a tour name.
- **active_marker**: Sets which ArUco marker is active for pose calculations.
- **get_aruco_pose**: Gets and saves the pose of an ArUco marker relative to the robot.
- **save_offset_pose**: Calculates and saves the offset between the robot’s current pose and an ArUco marker.
- **calculate_offset_pose**: Calculates the relative position of a target with respect to an ArUco marker.
---
# Demo Skills

## **[Demo and Advanced Skills](https://github.com/skyequack/Skills?tab=readme-ov-file#demo-and-advanced-skills-1)**

- **auto_train**: Trains a new object detection model via the webapp. Captures images, labels the object, and optionally forgets old objects. Automates dataset creation and model training for new objects.
- **update_ply_file**: Updates the background projection or simulation environment for the Dalus viewer by setting a new PLY file and pose.
- **auto_scan**: Starts an automated scanning routine for an object, moving the robot through calculated waypoints to capture images for training.
- **aruco_testing**: Tests ArUco marker offset calculation. Moves the robot to specific poses, calculates offsets, and demonstrates pose transitions using ArUco markers.
- **control_chuck**: Activates or deactivates the robot's chuck (gripper), supporting pneumatic and robotiq models. Can open/close the chuck and set the stroke length for robotiq grippers.
- **drilling**: Executes a full drilling workflow on an object. Includes picking, placing, tool rotation, object counting, and error handling using vision and feedback. Integrates with ArUco-based localization and multiple robot actions.
- **feedback_loop**: Runs a feedback-based pick-and-place loop. Counts objects, attempts to pick and place with retries, and uses vision to verify object presence at each step. Provides robust error handling and user feedback.
- **segmentation_check**: Checks image segmentation and moves the robot to the pose of a segmented object. Useful for validating vision-based object localization and robot movement.

## [Bottle serve](https://github.com/skyequack/Skills?tab=readme-ov-file#Bottle%20serve-1)

- **move_to_pose**: Moves the robot to a specified named pose using the robot movement service.
- **control_gripper**: Opens or closes the robot’s gripper using the gripper service.
- **execute_serving**: Executes a full bottle serving sequence, including picking up bottles from predefined locations, serving them, and returning the robot to home positions.

## [Pick and Place](https://github.com/skyequack/Skills?tab=readme-ov-file#Pick%20and%20Place-1)

- **pick_object: Picks up a specified object using the robot. Moves to the home position, detects the object's pose, closes the gripper to grasp the object, and moves to an intermediate or home position.
- **place_object**: Places an object at a specified pose, on a target object, or in a specified direction. Moves to the drop location, opens the gripper to release the object, and returns to the home position.
- **clean_table**: Picks up all detected objects (except the bucket) from the workspace and places them in the bin or bucket, effectively cleaning the table.

---

# Robot State and Movement

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

# Object and Vision Skills

### **get_best_match**
**Description:**  
Finds and returns the best-matching object name from a list, using string similarity (e.g., fuzzy matching).

**Parameters:**  
- `object_list` (list of str): List of available object names.  
- `target_name` (str): The name to match against the list.

**Returns:**  
- `str`: The best-matching object name.

**Usage Example:**  
```python
best_match = get_best_match()._run(object_list=["cup", "bottle", "box"], target_name="bttle")
```

---

### **get_object_list**
**Description:**  
Returns the list of objects currently detectable by the robot’s vision system.

**Parameters:**  
- None.

**Returns:**  
- `list` of `str`: Names of detected or known objects.

**Usage Example:**  
```python
objects = get_object_list()._run()
```

---

### **check_pose**
**Description:**  
Gets the position (pose) of a specified object in the robot’s workspace using the vision system.

**Parameters:**  
- `object_name` (str): Name of the object to locate.

**Returns:**  
- `list` or `dict`: The pose of the object (e.g., `[x, y, z, rx, ry, rz]`).

**Usage Example:**  
```python
pose = check_pose()._run(object_name="bottle")
```

---

### **analyze_camera_frame**
**Description:**  
Analyzes the current camera frame using a prompt (e.g., for OCR, object detection, or other vision tasks).

**Parameters:**  
- `prompt` (str): Instruction for the analysis (e.g., "read the label", "find the red object").  
- `camera_id` (str, optional): Which camera to use.

**Returns:**  
- `str` or `dict`: Result of the analysis (e.g., detected text, object info).

**Usage Example:**  
```python
result = analyze_camera_frame()._run(prompt="read the serial number")
```

---

### **set_context_camera**
**Description:**  
Sets which camera should be used for context or detection tasks.

**Parameters:**  
- `camera_id` (str): Identifier for the camera to set as active.

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
set_context_camera()._run(camera_id="camera_2")
```

---

### **compare_images**
**Description:**  
Compares two images and returns the difference or similarity, possibly using a prompt for specific comparison criteria.

**Parameters:**  
- `image1` (str or image object): First image to compare.  
- `image2` (str or image object): Second image to compare.  
- `prompt` (str, optional): Instruction for the comparison (e.g., "find differences", "check for missing parts").

**Returns:**  
- `str` or `dict`: Result of the comparison (e.g., difference score, highlighted regions).

**Usage Example:**  
```python
comparison = compare_images()._run(image1="img1.png", image2="img2.png", prompt="highlight changes")
```

---

# Utility Skills
### **industry_test**
**Description:**  
Runs a test routine by moving the robot through a list of poses for a specified number of cycles. Useful for industrial validation or endurance testing.

**Parameters:**  
- `pose_list` (list of poses): List of poses to cycle through.  
- `cycles` (int): Number of times to repeat the sequence.

**Returns:**  
- `str`: Status message indicating completion or errors.

**Usage Example:**  
```python
industry_test()._run(pose_list=[pose1, pose2, pose3], cycles=5)
```

---

### **recording_object**
**Description:**  
Moves the robot through a set of named poses, possibly for data collection, demonstration, or recording object positions.

**Parameters:**  
- `pose_names` (list of str): Names of poses to visit in sequence.

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
recording_object()._run(pose_names=["start", "mid", "end"])
```

---

### **custom_tour**
**Description:**  
Executes a custom sequence of actions (tour) based on a provided tour name. Useful for demonstrations or guided workflows.

**Parameters:**  
- `tour_name` (str): Name of the custom tour to execute.

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
custom_tour()._run(tour_name="factory_overview")
```

---

### **active_marker**
**Description:**  
Sets which ArUco marker is active for pose calculations, enabling the robot to reference a specific marker for spatial tasks.

**Parameters:**  
- `marker_id` (int or str): Identifier of the ArUco marker to activate.

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
active_marker()._run(marker_id=23)
```

---

### **get_aruco_pose**
**Description:**  
Retrieves and saves the pose of a specified ArUco marker relative to the robot, useful for calibration or localization.

**Parameters:**  
- `marker_id` (int or str): Identifier of the ArUco marker.

**Returns:**  
- `list` or `dict`: The pose of the marker.

**Usage Example:**  
```python
pose = get_aruco_pose()._run(marker_id=42)
```

---

### **save_offset_pose**
**Description:**  
Calculates and saves the offset between the robot’s current pose and a specified ArUco marker, useful for repeatable positioning.

**Parameters:**  
- `marker_id` (int or str): Identifier of the ArUco marker.  
- `offset_name` (str): Name to save the offset under.

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
save_offset_pose()._run(marker_id=42, offset_name="bin_offset")
```

---

### **calculate_offset_pose**
**Description:**  
Calculates the relative position (offset) of a target with respect to an ArUco marker, aiding in precise placement or manipulation.

**Parameters:**  
- `marker_id` (int or str): Identifier of the ArUco marker.  
- `target_pose` (list or dict): The pose of the target to compare.

**Returns:**  
- `list` or `dict`: The calculated offset.

**Usage Example:**  
```python
offset = calculate_offset_pose()._run(marker_id=42, target_pose=[...])
```

---

# Demo and Advanced Skills

### **auto_train**
**Description:**  
Trains a new object detection model via the webapp. The robot captures images of a specified object, labels it, and can optionally forget previously learned objects. Automates dataset creation and model training for new objects.

**Parameters:**  
- `object_to_look` (str): The object the robot should focus on for training.
- `object_name` (str): The label to assign to the object.
- `forget_old` (bool, default=True): If True, forgets all previously trained objects.
- `images_to_train` (int, default=100): Number of images to capture for training.
- `number_of_epochs` (int, default=30): Number of training epochs.

**Returns:**  
- `str`: Status message indicating training progress or completion.

**Usage Example:**  
```python
auto_train()._run(
    object_to_look="cup",
    object_name="coffee_cup",
    forget_old=True,
    images_to_train=120,
    number_of_epochs=40
)
```

---

### **update_ply_file**
**Description:**  
Updates the background projection or simulation environment for the Dalus viewer by setting a new PLY file and pose.

**Parameters:**  
- (Parameters not explicitly defined in the snippet, but likely include the PLY file path and pose information.)

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
update_ply_file()._run(ply_file_path="scene.ply", pose=[...])
```

---

### **auto_scan**
**Description:**  
Starts an automated scanning routine for an object, moving the robot through calculated waypoints to capture images for training or inspection.

**Parameters:**  
- (Parameters not explicitly defined in the snippet, but likely include object name, scan area, and number of waypoints.)

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
auto_scan()._run(object_name="box", waypoints=12)
```

---

### **aruco_testing**
**Description:**  
Tests ArUco marker offset calculation. Moves the robot to specific poses, calculates offsets, and demonstrates pose transitions using ArUco markers.

**Parameters:**  
- (Parameters not explicitly defined in the snippet, but likely include marker ID and test configuration.)

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
aruco_testing()._run(marker_id=7)
```

---

### **control_chuck**
**Description:**  
Activates or deactivates the robot's chuck (gripper), supporting pneumatic and robotiq models. Can open/close the chuck and set the stroke length for robotiq grippers.

**Parameters:**  
- `action` (str): "open" or "close".
- `gripper_type` (str, optional): Type of chuck/gripper.
- `stroke` (float, optional): Stroke length for robotiq grippers.

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
control_chuck()._run(action="close", gripper_type="robotiq", stroke=0.5)
```

---

### **drilling**
**Description:**  
Executes a full drilling workflow on an object. Includes picking, placing, tool rotation, object counting, and error handling using vision and feedback. Integrates with ArUco-based localization and multiple robot actions.

**Parameters:**  
- (Parameters not explicitly defined in the snippet, but likely include object name, drill position, and feedback options.)

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
drilling()._run(object_name="panel", drill_depth=10)
```

---

### **feedback_loop**
**Description:**  
Runs a feedback-based pick-and-place loop. Counts objects, attempts to pick and place with retries, and uses vision to verify object presence at each step. Provides robust error handling and user feedback.

**Parameters:**  
- (Parameters not explicitly defined in the snippet, but likely include object name, max retries, and feedback criteria.)

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
feedback_loop()._run(object_name="bottle", max_retries=3)
```

---

### **segmentation_check**
**Description:**  
Checks image segmentation and moves the robot to the pose of a segmented object. Useful for validating vision-based object localization and robot movement.

**Parameters:**  
- `object_name` (str): Name of the object to segment and locate.

**Returns:**  
- `str`: Status message.

**Usage Example:**  
```python
segmentation_check()._run(object_name="box")
```

---

# Bottle Serve

### **move_to_pose**
**Description:**  
Moves the robot to a specified named pose using the robot movement service. Used for navigating to pick, serve, or home positions during the bottle serving sequence.

**Parameters:**  
- `pose_name` (str): The name of the pose to move the robot to.

**Returns:**  
- `str`: Status message indicating the result of the movement.

**Usage Example:**  
```python
controller.move_to_pose("home")
```

---

### **control_gripper**
**Description:**  
Opens or closes the robot’s gripper using the gripper service. Used to grasp or release bottles during the serving process.

**Parameters:**  
- `close` (bool): If True, closes the gripper to grasp an object; if False, opens the gripper to release.

**Returns:**  
- `str`: Status message indicating the result of the gripper action.

**Usage Example:**  
```python
controller.control_gripper(True)   # Close gripper (grab bottle)
controller.control_gripper(False)  # Open gripper (release bottle)
```

---

### **execute_serving**
**Description:**  
Executes the full bottle serving sequence. The robot moves through a series of predefined poses to pick up bottles, serve them at target locations, and return to home positions, using the gripper to grasp and release bottles as needed.

**Parameters:**  
- None.

**Returns:**  
- `str`: Status message indicating the result of the serving sequence.

**Usage Example:**  
```python
controller.execute_serving()
```

---

# Pick and Place

### **pick_object**
**Description:**  
Picks up a specified object using the robot. The robot moves to the object's location, closes the gripper to grasp the object, and may move to an intermediate or home position after picking.

**Parameters:**  
- `object` (str): The name of the object the robot needs to pick up.
- `robot_to_use` (int, default=1): The robot number to use for this task.

**Returns:**  
- `str`: Status message indicating the result of the pick operation.

**Usage Example:**  
```python
pick_object()._run(object="bottle", robot_to_use=1)
```

---

### **place_object**
**Description:**  
Places an object at a specified pose, on a target object, or in a specified direction. The robot moves to the drop location, opens the gripper to release the object, and may return to the home position.

**Parameters:**  
- `drop_name` (str, optional): The name of the pose where the robot should place the object.
- `drop_object` (str, optional): The object on which to place the item.
- `robot_to_use` (int, default=1): The robot number to use for this task.
- `direction` (str, optional): The direction in which to place the object.

**Returns:**  
- `str`: Status message indicating the result of the place operation.

**Usage Example:**  
```python
place_object()._run(drop_name="bin_pose", drop_object="bin", robot_to_use=1, direction="left")
```

---

### **clean_table**
**Description:**  
Cleans the table by picking up all detected objects (except the bin or bucket) from the workspace and placing them in the bin or bucket, effectively clearing the workspace.

**Parameters:**  
- none
	
**Returns:**  
- `str`: Status message indicating the result of the cleaning operation.

**Usage Example:**  
```python
clean_table()._run()
```

---
