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