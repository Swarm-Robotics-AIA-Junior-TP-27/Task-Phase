# Task 3 — ROS 2 Communication and Drone Sensor Monitoring

## Objective

In this task, you will learn how to develop a basic robotic software system using **ROS 2 Jazzy and Python**.

Modern autonomous robots and drones consist of multiple software components that must communicate with one another. Sensor information must be collected, processed, monitored, and communicated between different parts of the system.

ROS 2 provides a framework for building such distributed robotic applications.

You will develop a **simulated drone telemetry and monitoring system** using ROS 2.

By the end of this task, you should understand:

- How ROS 2 nodes work
- How different nodes communicate using topics
- The publisher–subscriber communication model
- ROS 2 message types
- Publishing data at a fixed frequency
- Processing sensor information
- Implementing basic monitoring and warning logic
- Using ROS 2 command-line tools to inspect a running system
- Creating and organizing ROS 2 Python packages

**Important:** This task does not require an actual drone, flight controller, Gazebo, or ArduPilot/PX4 simulation. All sensor data will be simulated using Python.

---

## 1. ROS 2 Fundamentals

Before starting the implementation, study the following ROS 2 concepts.

### 1.1 ROS 2 Nodes

Understand:

- What a ROS 2 node is
- Why robotic applications use multiple nodes
- How nodes execute independently
- How nodes communicate with one another

### 1.2 Topics and Messages

Study:

- What a ROS 2 topic is
- Publisher and subscriber concepts
- How messages are transferred between nodes
- The difference between a topic name and a message type

### 1.3 Timers and Publishing Frequency

Understand:

- How ROS 2 timers work
- Publishing data periodically
- The meaning of frequency in Hz
- How publishing frequency affects communication

### 1.4 ROS 2 Workspace and Packages

Learn:

- ROS 2 workspace structure
- Python packages using `ament_python`
- Purpose of `package.xml`
- Purpose of `setup.py`
- Building packages using `colcon`
- Sourcing the workspace
- Running nodes using `ros2 run`

You should understand these concepts before beginning the implementation.

---

## 2. System Overview

You are required to develop a simulated drone telemetry system.

The system will consist of three main ROS 2 nodes:

1. **Sensor Publisher Node**
2. **Telemetry Monitor Node**
3. **Warning Publisher Node**

The nodes will communicate using ROS 2 topics.

### 2.1 Expected System Architecture

```text
        Sensor Publisher
               |
               | /drone/altitude
               | /drone/battery
               | /drone/temperature
               |
               v
        Telemetry Monitor
               |
               | /drone/status
               v
        Warning Publisher
               |
               | /drone/warnings
               v
         ROS 2 Terminal
```

This diagram represents the intended data flow. You are expected to implement the communication between these nodes.

---

## 3. Sensor Publisher Node

Create a ROS 2 Python node called:

`drone_sensor_publisher`

This node will simulate three types of drone sensor information.

### 3.1 Altitude

Publish simulated altitude readings in meters.

Topic:

`/drone/altitude`

Message type:

`std_msgs/msg/Float32`

Altitude values should change over time to represent a drone gaining or losing altitude.

### 3.2 Battery Percentage

Publish simulated battery readings.

Topic:

`/drone/battery`

Message type:

`std_msgs/msg/Float32`

Battery percentage should gradually decrease over time to simulate battery consumption.

Keep the value between 0 and 100.

### 3.3 Temperature

Publish simulated onboard temperature readings in degrees Celsius.

Topic:

`/drone/temperature`

Message type:

`std_msgs/msg/Float32`

Temperature readings should change during execution.

### 3.4 Publishing Requirements

The node must:

- Publish all three sensor values
- Use a ROS 2 timer
- Publish readings at a frequency of 1 Hz
- Generate changing sensor values
- Continue publishing until the node is stopped

You may use mathematical functions, random values, or other Python logic to simulate realistic sensor changes.

The sensor values must be generated programmatically rather than entered manually for each reading.

---

## 4. Telemetry Monitor Node

Create a second ROS 2 Python node called:

`drone_telemetry_monitor`

This node will subscribe to all three sensor topics.

### 4.1 Subscriber Requirements

Subscribe to:

- `/drone/altitude`
- `/drone/battery`
- `/drone/temperature`

The node should continuously receive and store the latest sensor values.

### 4.2 Telemetry Display

Display the latest received telemetry information in the terminal approximately once every second.

Example:

```text
Drone Telemetry

Altitude       : 12.5 m
Battery        : 78.0 %
Temperature    : 42.3 °C
```

The displayed values should update as new sensor messages arrive.

### 4.3 Drone Status

The telemetry monitor should determine a general drone status based on the available sensor information.

Use the following conditions:

| Condition | Drone Status |
| --- | --- |
| All sensor values within limits | NORMAL |
| Battery below 20% | LOW BATTERY |
| Temperature above 60°C | OVERHEATING |
| Altitude above 30 m | ALTITUDE LIMIT EXCEEDED |

Multiple abnormal conditions may exist at the same time. Your implementation should be capable of identifying all active conditions.

### 4.4 Status Publisher

The telemetry monitor must publish the current status to:

`/drone/status`

Message type:

`std_msgs/msg/String`

Examples:

```text
NORMAL
```

```text
LOW BATTERY
```

```text
LOW BATTERY, OVERHEATING
```

The status should be published at 1 Hz.

If one or more sensor values have not yet been received, the node should report `WAITING FOR SENSOR DATA` instead of assuming that the drone is operating normally.

---

## 5. Warning Publisher Node

Create a third ROS 2 Python node called:

`drone_warning_publisher`

This node will monitor the drone status published by the telemetry monitor.

### 5.1 Status Subscription

Subscribe to:

`/drone/status`

Message type:

`std_msgs/msg/String`

### 5.2 Warning Generation

Whenever an abnormal drone status is received, generate a corresponding warning.

Examples:

```text
[WARNING] Battery level is critically low!
```

```text
[WARNING] Drone temperature exceeds safe limit!
```

```text
[WARNING] Drone altitude exceeded the configured limit!
```

The warning node must support multiple warnings if multiple abnormal conditions are reported.

### 5.3 Warning Topic

Publish the generated warnings on:

`/drone/warnings`

Message type:

`std_msgs/msg/String`

When the status is `NORMAL`, publish:

```text
No active warnings
```

When the status is `WAITING FOR SENSOR DATA`, publish:

```text
Waiting for telemetry
```

Warning messages should be displayed in the terminal and should also be available through the ROS 2 warning topic.

---

## 6. ROS 2 Command-Line Tools

After implementing the three nodes, use ROS 2 command-line tools to inspect the running system.

Demonstrate the use of:

### 6.1 Node Inspection

```bash
ros2 node list
```

Identify the nodes running in your system.

### 6.2 Topic Inspection

```bash
ros2 topic list
```

Identify the topics being used for communication.

### 6.3 Topic Information

```bash
ros2 topic info /drone/altitude
```

Determine the publisher and subscriber counts.

### 6.4 Message Inspection

```bash
ros2 topic echo /drone/battery
```

Observe the battery data being published.

### 6.5 Publishing Frequency

```bash
ros2 topic hz /drone/altitude
```

Verify that the publisher operates at approximately 1 Hz.

### 6.6 Node Information

```bash
ros2 node info /drone_telemetry_monitor
```

Inspect its publishers and subscribers.

---

## 7. ROS 2 Communication Graph

Use `rqt_graph` to visualize the communication between your ROS 2 nodes.

The graph should clearly show:

- Sensor Publisher Node
- Telemetry Monitor Node
- Warning Publisher Node
- Their respective topics
- The direction of communication

Capture a screenshot of the communication graph.

Explain how information travels from the sensor publisher to the warning publisher.

---

## 8. Testing and Validation

Your system must be tested under different simulated conditions.

Demonstrate the following test cases.

| Test | Simulated Condition | Expected Result |
| --- | --- | --- |
| 1 | All values within limits | NORMAL |
| 2 | Battery below 20% | Low battery warning |
| 3 | Temperature above 60°C | Overheating warning |
| 4 | Altitude above 30 m | Altitude warning |
| 5 | Two or more limits exceeded | Multiple warnings |
| 6 | Sensor publisher not running | Waiting for sensor data at startup |

You may modify the simulated sensor values or their initial conditions to demonstrate these cases.

For each test, capture the relevant terminal output or screenshot.

**Note:** The waiting-for-data behavior is required during startup before the first sensor readings are received. Handling sensors that stop publishing after previously working is optional.

---

## 9. ROS 2 Package Organization

Create a ROS 2 Python package named:

`drone_monitoring`

The package should contain the three executable nodes.

Recommended structure:

```text
drone_monitoring/
│
├── package.xml
├── setup.py
├── setup.cfg
│
├── resource/
│   └── drone_monitoring
│
├── drone_monitoring/
│   ├── __init__.py
│   ├── sensor_publisher.py
│   ├── telemetry_monitor.py
│   └── warning_publisher.py
│
└── test/
```

All three nodes must be executable using `ros2 run`.

The Python code should be organized, readable, and appropriately documented.

---

## 10. README Documentation

Prepare a `README.md` explaining your implementation.

Your README must contain:

1. **Project Overview:** Brief explanation of the system and its purpose.
2. **System Architecture:** Diagram showing nodes, topics, and their connections.
3. **ROS 2 Package Structure:** Description of the important files.
4. **Implementation:** Explanation of how each node works.
5. **Instructions to Run:** Commands required to build and execute the package.
6. **Testing:** Results of the test cases in Section 8.
7. **Screenshots:** Terminal outputs and ROS 2 communication graph.
8. **Challenges and Learning:** Problems encountered and how they were resolved.

---

## 11. Submission Requirements

Complete the task inside a `Task3` folder in your personal Task-Phase GitHub repository.

Recommended structure:

```text
Task3/
│
├── README.md
│
├── drone_monitoring/
│   ├── package.xml
│   ├── setup.py
│   ├── setup.cfg
│   ├── resource/
│   │   └── drone_monitoring
│   ├── drone_monitoring/
│   │   ├── __init__.py
│   │   ├── sensor_publisher.py
│   │   ├── telemetry_monitor.py
│   │   └── warning_publisher.py
│   └── test/
│
└── screenshots/
    ├── normal_operation.png
    ├── low_battery_warning.png
    ├── overheating_warning.png
    ├── altitude_warning.png
    ├── multiple_warnings.png
    └── ros2_graph.png
```

Do not include generated ROS 2 build directories, installation directories, or log files in your GitHub repository.
