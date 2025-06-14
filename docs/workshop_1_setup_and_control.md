# Workshop 1: Robot Setup & Control

This document outlines the slides for the first workshop session.

---

### **Slide 1: Title Slide**

*   **Title**: Workshop 1: Robot Setup & Control
*   **Subtitle**: From Box to Action

---

### **Slide 2: Agenda**

*   **Title**: What We'll Cover Today
*   **Content**:
    1.  The Documentation: Your Best Friend
    2.  Finding Your Robot's Port
    3.  Calibration: The First, Crucial Step
    4.  Teleoperation: Taking Direct Control

---

### **Slide 3: Your Most Important Tab**

*   **Content**: (Displayed prominently)
    ```
    https://huggingface.co/docs/lerobot/index
    ```
*   **Notes**: "This is your single source of truth. Keep it open. It has everything we'll cover and more."

---

### **Slide 4: Step 1 - Finding Your Robot's Port**

*   **Title**: Step 1: Finding Your Robot's Port
*   **Goal**: Identify the unique USB port for *each* arm (the follower/robot and the leader/controller).
*   **The Command**:
    ```bash
    python lerobot/find_port.py
    ```
*   **The Process (It's Interactive!)**:
    1.  The script will list all connected serial ports.
    2.  It will then ask you to **unplug one arm** (e.g., the follower) and press Enter.
    3.  The script identifies which port disappeared from the list. **That's the port for the arm you unplugged!**
    4.  Reconnect the arm. You can run the script again to identify the other arm's port.
*   **Action**: Note down the specific port for your follower arm and your leader arm. You will need them for calibration.

---

### **Slide 5: Step 2 - What is Calibration?**

*   **Title**: What is Calibration?
*   **Concept**: Teaching the software the physical limits and properties of your specific robot arms.
*   **Why it's CRUCIAL**: Without calibration, movements will be inaccurate, unpredictable, and potentially unsafe for the hardware. You do this ONCE per robot setup.

---

### **Slide 6: Calibrating the Follower Arm (The Robot)**

*   **Title**: Calibrating the Follower Arm
*   **Command Breakdown**:
    ```bash
    python -m lerobot.calibrate \
           --robot.type=so101_follower \
           --robot.port=YOUR_FOLLOWER_PORT \
           --robot.id='your-robot-name'
    ```
*   **Notes**: Explain each argument:
    *   `--robot.type`: Specifies the kind of robot.
    *   `--robot.port`: The port you found in Step 1.
    *   `--robot.id`: Give your robot a unique name. This saves the calibration file under that name.

---

### **Slide 7: Calibrating the Leader Arm (The Controller)**

*   **Title**: Calibrating the Leader Arm
*   **Command Breakdown**:
    ```bash
    python -m lerobot.calibrate \
           --teleop.type=so101_leader \
           --teleop.port=YOUR_LEADER_PORT \
           --teleop.id='your-controller-name'
    ```
*   **Notes**: Explain the `--teleop` prefix, which signifies this is the teleoperation/controller device.

---

### **Slide 8: Step 3 - Teleoperation: Taking Control**

*   **Title**: Step 3: Taking Direct Control
*   **Goal**: Drive the robot arm manually using the leader arm controller. This is how you'll record data for imitation learning.
*   **Reference**: "For more details, see the 'Imitation Learning for Robots' tutorial in the main LeRobot documentation."

---

### **Slide 9: The Teleoperation Command**

*   **Title**: The Teleoperation Command
*   **Command Breakdown**:
    ```bash
    python -m lerobot.teleoperate \
           --robot.type=so101_follower \
           --robot.port=YOUR_FOLLOWER_PORT \
           --robot.id=your-robot-name \
           --teleop.type=so101_leader \
           --teleop.port=YOUR_LEADER_PORT \
           --teleop.id=your-controller-name
    ```
*   **Notes**: "We are now using the IDs for both the robot and the controller that we defined during calibration."

---

### **Slide 10: Live Demo**

*   **Title**: Live Demo Time!
*   **Content**: (This slide is a cue for the instructor).
*   **Notes**: "Let's run through `find_port`, `calibrate`, and `teleoperate` live."

---

### **Slide 11: Common Issues & Troubleshooting**

*   **Title**: Quick Troubleshooting
*   **Content**:
    *   **"Can't find port?"**: Make sure the robot is plugged in and turned on. Run `find_port.py` again.
    *   **"Calibration fails?"**: Check your IDs and ports. Ensure the robot has clear space to move.
    *   **"Movement is jerky?"**: You might need to re-calibrate. Follow all on-screen steps carefully.

---

### **Slide 12: Q&A and Hands-on Time**

*   **Title**: Your Turn!
*   **Content**: "Find your ports, calibrate your arms, and try teleoperation. Mentors are here to help." 