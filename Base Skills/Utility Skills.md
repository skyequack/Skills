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