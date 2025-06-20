## **[[Demo and Advanced Skills]]**
[Demo and Advanced Skills](https://github.com/skyequack/Skills/blob/main/Demo%20and%20Advanced%20Skills.md)

- **auto_train**: Trains a new object detection model via the webapp. Captures images, labels the object, and optionally forgets old objects. Automates dataset creation and model training for new objects.
- **update_ply_file**: Updates the background projection or simulation environment for the Dalus viewer by setting a new PLY file and pose.
- **auto_scan**: Starts an automated scanning routine for an object, moving the robot through calculated waypoints to capture images for training.
- **aruco_testing**: Tests ArUco marker offset calculation. Moves the robot to specific poses, calculates offsets, and demonstrates pose transitions using ArUco markers.
- **control_chuck**: Activates or deactivates the robot's chuck (gripper), supporting pneumatic and robotiq models. Can open/close the chuck and set the stroke length for robotiq grippers.
- **drilling**: Executes a full drilling workflow on an object. Includes picking, placing, tool rotation, object counting, and error handling using vision and feedback. Integrates with ArUco-based localization and multiple robot actions.
- **feedback_loop**: Runs a feedback-based pick-and-place loop. Counts objects, attempts to pick and place with retries, and uses vision to verify object presence at each step. Provides robust error handling and user feedback.
- **segmentation_check**: Checks image segmentation and moves the robot to the pose of a segmented object. Useful for validating vision-based object localization and robot movement.
