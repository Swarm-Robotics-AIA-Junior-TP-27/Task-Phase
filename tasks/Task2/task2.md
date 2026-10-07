# Task 2 — Drone Electronics, Sensors & System Architecture

In this task, you will study the **electronic components, sensors, communication interfaces, and overall system architecture used in modern drones and autonomous robotic systems**.

The objective is not only to identify individual components, but also to understand:

- What each component does
- How it works
- Why it is required
- What information it provides
- How different components communicate with each other
- How all components together form a complete autonomous drone system

By the end of this task, you should be able to look at a drone architecture and explain how power, control commands, sensor data, and telemetry flow through the system.

---

## 1. Drone System Overview

Before studying individual components, understand the basic architecture of a multirotor drone.

Learn the roles of:

- Flight Controller
- Electronic Speed Controllers
- Brushless Motors
- Propellers
- Battery
- Power Module / Power Distribution
- GPS
- RC Receiver
- Telemetry System
- Companion Computer
- Sensors
- Ground Control Station

Understand the difference between:

- Flight Controller and Companion Computer
- RC communication and telemetry communication
- Manual flight and autonomous flight
- Sensors used for stabilization and sensors used for perception

---

## 2. Electronic Components

Study the following major components used in drone systems.

### 2.1 Flight Controller

Research:

- What a Flight Controller is
- Main responsibilities of a Flight Controller
- How it stabilizes a drone
- Sensors commonly available inside a Flight Controller
- Flight modes
- Motor output/control
- Failsafe handling

Also understand the difference between:

- Flight Controller hardware
- Flight-control firmware

Examples of flight-control firmware:

- ArduPilot
- PX4

You may also explore examples of Flight Controller hardware used in real drone systems.

---

### 2.2 Electronic Speed Controller — ESC

Study:

- Purpose of an ESC
- How an ESC controls a brushless motor
- How the Flight Controller communicates with an ESC
- PWM and digital ESC protocols at a basic level
- Current and voltage ratings
- Individual ESC vs 4-in-1 ESC

Understand the basic factors considered while selecting an ESC.

---

### 2.3 Brushless Motors and Propellers

---

### 2.4 Battery and Power System

---

### 2.5 GPS and GNSS

Study:

- How GPS/GNSS positioning works at a basic level
- Latitude
- Longitude
- Altitude
- Satellite-based positioning
- Position accuracy

Understand the role of GPS in:

- Position Hold
- Waypoint navigation
- Return-to-Home
- Autonomous missions

Also understand:

- What RTK GPS is
- Basic difference between standard GPS and RTK GPS

---

### 2.6 RC Transmitter and Receiver

Understand the basic purpose of the RC system in a drone.

Study:

- RC transmitter
- RC receiver
- Channels
- Pilot control inputs
- Arm/disarm controls
- Flight mode controls
- Failsafe
- Basic idea of systems such as ELRS

Also understand the difference between:

- RC communication
- Telemetry communication

Detailed study of RC communication protocols is not required.

---

### 2.7 Companion Computer

Study the purpose of an onboard or companion computer.

Examples include:

- Raspberry Pi
- NVIDIA Jetson

Understand why a companion computer may be required even when a drone already has a Flight Controller.

Research applications such as:

- Computer vision
- Object detection
- Path planning
- Autonomous decision making
- ROS 2
- Machine learning

Understand the basic architecture:

```text
Sensors / Camera
       │
       ↓
Companion Computer
       │
    MAVLink
       │
       ↓
Flight Controller
       │
       ↓
      ESCs
       │
       ↓
     Motors
```

---

## 3. Sensors

Study the following sensors and understand their role in drone and robotic systems.

### 3.1 IMU

Study:

- Accelerometer
- Gyroscope

Understand:

- What each sensor measures
- Why both are required
- How IMU data is useful for drone stabilization and orientation estimation

---

### 3.2 Magnetometer

Study:

- What a magnetometer measures
- How it is used to estimate heading
- Sources of magnetic interference

---

### 3.3 Barometer

Study:

- Atmospheric pressure
- Altitude estimation
- Why barometer readings may not perfectly represent true altitude

---

### 3.4 LiDAR

Study:

- Working principle
- Distance measurement
- 2D LiDAR
- 3D LiDAR

Understand its applications in:

- Obstacle detection
- Mapping
- Localization
- Altitude measurement
- Environment perception

Explain its major advantages and limitations.

---

### 3.5 Depth Camera

Study:

- What depth information represents
- RGB-D cameras
- Basic methods used to obtain depth information

Understand applications such as:

- Obstacle detection
- Mapping
- Object distance estimation
- Environment perception

Research at least one real depth camera used in robotics.

---

### 3.6 Optical Flow Sensor

Study:

- Basic principle of optical flow
- How motion can be estimated from changes between images
- Why optical flow may be useful indoors or in GPS-denied environments

Understand some of its limitations, including:

- Poor lighting
- Low-texture surfaces
- High altitude

---

## 4. Additional Sensor Research

Choose at least **two additional sensors or sensing technologies** that may be useful in autonomous drones.

Possible application areas include:

- Obstacle detection
- Navigation
- Localization
- Environmental sensing
- Search and rescue
- Human detection
- Mapping

For each selected technology, explain:

- Working principle
- Application
- Advantages
- Limitations

You are encouraged to explore sensors beyond the examples listed above.

---

## 5. Communication Interfaces

Study the basic purpose of the following interfaces commonly encountered in robotic and drone systems:

- UART
- I2C
- SPI
- CAN
- PWM
- USB

You are **not expected to study the electrical protocol in depth**.

Instead, understand:

- What each interface is used for
- What types of devices commonly use it
- Examples of where it may appear in a drone system

Create a table similar to:

| Interface | Typical Use | Example Device |
| --- | --- | --- |
| UART |  |  |
| I2C |  |  |
| SPI |  |  |
| CAN |  |  |
| PWM |  |  |
| USB |  |  |

---

## 6. System Architecture

Create a **complete system architecture diagram for an autonomous quadcopter**.

Your architecture should include at least:

- Battery
- Power system
- Flight Controller
- ESCs
- Motors
- GPS
- IMU
- RC Receiver
- Companion Computer
- Camera
- LiDAR or depth sensor
- Ground Control Station

Clearly show how the components are connected.

For important connections, indicate what is being transferred.

Examples:

- Power
- Sensor data
- Motor commands
- MAVLink messages
- RC commands
- Image/video data
- Telemetry

The objective is to demonstrate that you understand **how individual components combine to form a complete drone system**.

---

## 7. Component Selection Problem

Consider that you are designing an autonomous drone for a **Search and Rescue mission**.

The drone should be capable of:

- Outdoor flight
- Waypoint navigation
- Obstacle detection
- Detecting or locating people
- Sending telemetry to a Ground Control Station
- Performing onboard image processing

Select suitable components or technologies for:

- Flight Controller
- Companion Computer
- Positioning system
- Obstacle-detection sensor
- Human-detection sensor/camera
- Communication system

You do not need to select the most expensive or most powerful hardware.

For each selection, briefly explain **why it would be suitable for the mission**.

The Component Selection Problem must be included inside the IEEE technical report as a separate section.

---

## 8. Technical Report

Prepare a technical report summarizing your research and findings.

The report should focus on **technical understanding rather than simply collecting definitions**.

For the major components and sensors, discuss where appropriate:

- Working principle
- Purpose
- Typical applications
- Advantages
- Limitations
- Integration considerations

Include suitable:

- Diagrams
- Tables
- Figures
- System architecture diagrams

The report must also include:

- The **System Architecture** from Section 6
- The **Component Selection Problem** from Section 7

Whenever external material is used, properly cite the source.

---

## 9. Report Format

The technical report must follow the **IEEE conference format**.

IEEE conference template:

[IEEE Conference Template — Overleaf](https://www.overleaf.com/latex/templates/ieee-conference-template/grfzhhncsfqn)

The report should contain:

- Title
- Abstract
- Introduction
- Technical Sections
- System Architecture
- Component Selection
- Conclusion
- References

---

## 10. Folder Structure

Complete the task inside a `Task2` folder in your personal task-phase GitHub repository.

Recommended structure:

```text
Task2
│
├── Drone_Electronics_Report.pdf
│
└── architecture
    └── drone_system_architecture.png
```

The architecture diagram must also be included inside the IEEE report.

Additional supporting files may be included if required.

---

## 11. Submission

Before submitting, ensure that the completed `Task2` folder has been committed and pushed to your GitHub repository.

Your submission must contain at minimum:

- `Drone_Electronics_Report.pdf`
- The System Architecture diagram
- The Component Selection Problem from Section 7 inside the report
- Proper references and citations

Once your work is complete:

1. Commit and push the completed `Task2` folder to your GitHub repository.
2. Go to the official **Task-Phase repository**.
3. Open **Issues → New Issue → Task Submission**.
4. Select **Task 2**.
5. Fill in the required details.
6. Provide the direct GitHub link to your `Task2` folder.
7. Submit the Issue Form.

Do **not** upload your completed report or task files directly to the central Task-Phase repository.

Your completed work should remain inside your own GitHub repository. The Issue Form is used only for submission and review.
