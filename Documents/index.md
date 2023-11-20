System Architecture
===================

System Diagram
--------------

![alternative text](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.github.com/MRCathRob/SystemIntegration/main/Documents/system_diagram.txt)


List of ROS Messages
--------------------

|Component   |Topic                        |Message  Type                 |Description                                                                                                                                                                    |Coordinate Frame|
|------------|-----------------------------|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|
|UI          |/subject/state/skin_entry    |geometry_msgs/msg/Point       |The needle entry point on the skin; measured by intraoperative images.                                                                                                         |Stage           |
|            |/subject/state/target        |geometry_msgs/msg/Point       |The target point in the subject; defined on intraoperative images.                                                                                                             |Stage           |
|            |/stage/cmd/parameters        |std_msgs/msg/String           |TBD                                                                                                                                                                            |                |
|            |/stage/cmd/control           |std_msgs/msg/String           |TBD                                                                                                                                                                            |                |
|Trajectory control            |/stage/state/needle_pose     |geometry_msgs/msg/PoseStamped        |The needle absolute insertion depth in the stage coordinate frame. In this implementation, the absolute depth is defined by y, while x- and z- positions are zero and the rotation is the unit quaternion (1,0,0,0).          |Stage           |
|            |/stage/control/cmd             |geometry_msgs/msg/PointStamped        |The desired stage pose to compensate needle tip error. In this implementation x- and z-positions are the desired horizonal and vertical of the stage, respectively. y-position in the desired insertion depth to be manually performed at the next insertion step |Stage          |
|Shape model |/needle/state/predicted_shape|geometry_msgs/msg/PoseArray   |The predicted needle shape as an array of positions and directions (i.e., poses) of needle sections (0.5-mm increment). **Not Implemented**                                    |Stage          |
|            |/needle/state/current_shape  |geometry_msgs/msg/PoseArray   |The estimated needle shape as an array of positions and directions (i.e., poses) of needle sections (0.5-mm increment).                                                        |Stage          |
|            |/needle/sensor/raw           |std_msgs/msg/Float64MultiArray|Raw FBG sensor data                                                                                                                                                            |Needle             |
|            |/needle/sensor/processed     |std_msgs/msg/Float64MultiArray|Processed FBG sensor data                                                                                                                                                      |Needle           |
|            |/needle/state/curvatures     |std_msgs/msg/Float64MultiArray|Curvatures measured from each of the active areas.                                                                                                                             |Needle
|Stage       |/needle/state/pose           |geometry_msgs/msg/PoseStamped        |The needle pose. In this implementation, the pose is defined only by the needle insertion depth (y) and the rotation about the y-axis. (x- z- translations and other rotations are zero).                                      |Stage          |
|            |/stage/state/pose            |geometry_msgs/msg/PoseStamped        |The pose of the stage. In this implementation, the pose is defined only by x- and z- translations. (y-translation and rotations are zero).                                     |Stage           |



Coordinate Systems
------------------


