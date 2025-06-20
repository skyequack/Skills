## **[[Robot State and Movement]]**
[Robot State and Movement](https://github.com/skyequack/Skills/blob/main/Robot%20State%20and%20Movement.md)
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
## **[[Object and Vision Skills]]**
[Object and Vision Skills](https://github.com/skyequack/Skills/blob/main/Object%20and%20Vision%20Skills.md)

- **get_best_match**: Finds the best-matching object name from a list using string similarity.
- **get_object_list**: Returns the list of detectable objects.
- **check_pose**: Gets the position of an object in the robot’s workspace using vision.
- **analyze_camera_frame**: Analyzes the camera feed with a prompt (can perform OCR).
- **set_context_camera**: Sets which camera is used for context or detection.
- **compare_images**: Compares two images and returns the difference based on a prompt.
## **[[Utility Skills]]**
[Utility Skills](https://github.com/skyequack/Skills/blob/main/Utility%20Skills.md)
- **industry_test**: Moves the robot through a list of poses for a number of cycles (for testing).
- **recording_object**: Moves the robot through a set of named poses, then returns home.
- **custom_tour**: Runs a custom tour (sequence of actions) based on a tour name.
- **active_marker**: Sets which ArUco marker is active for pose calculations.
- **get_aruco_pose**: Gets and saves the pose of an ArUco marker relative to the robot.
- **save_offset_pose**: Calculates and saves the offset between the robot’s current pose and an ArUco marker.
- **calculate_offset_pose**: Calculates the relative position of a target with respect to an ArUco marker.