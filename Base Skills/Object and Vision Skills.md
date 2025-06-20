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
