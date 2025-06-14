# Workshop 4: Learning from Experience (Reinforcement Learning)

This document outlines the detailed slides for the Reinforcement Learning workshop.

---

### **Slide 1: Title Slide**
- **Title**: Workshop 4: Learning from Experience
- **Subtitle**: Fine-tuning with Reinforcement Learning (HIL-SERL)

---

### **Slide 2: Agenda**
- **Title**: What We'll Cover
- **Content**:
    1.  When Imitation Isn't Enough
    2.  Intro to HIL-SERL: LeRobot's RL Workflow
    3.  The Core RL Loop & The Reward Function
    4.  The Actor-Learner Architecture
    5.  Pro-Tips: Key Hyperparameters
    6.  Capstone: The GR00T Recipe

---

### **Slide 3: When Imitation Isn't Enough**
- **Title**: The Limits of Imitation
- **Problem**: Your imitation-trained policy is good, but not perfect. It only knows what you showed it. It struggles with new situations and can't discover *better* ways to do the task.
- **Solution**: Reinforcement Learning (RL). Let the robot learn from its own trial-and-error to improve and perfect a skill.

---

### **Slide 4: LeRobot's RL Workflow: HIL-SERL**
- **Title**: Introducing HIL-SERL
- **Stands For**: **H**uman-**i**n-the-**L**oop **S**ample-**E**fficient **R**einforcement **L**earning.
- **What it is**: LeRobot's framework for making RL practical on real robots.
- **The Key Idea**: It's a hybrid approach! We don't start from scratch. We use your imitation learning dataset as a starting point, and then a human (you!) can intervene during live training to guide the robot, making the process much faster and safer.

---

### **Slide 5: The RL Loop & The Reward Function**
- **Title**: How a Robot *Really* Learns
- **The Loop**:
    - **Agent** (the policy) takes an `Action`.
    - `Action` affects the **Environment**.
    - Agent gets an `Observation` (from cameras) and a `Reward`.
- **The Reward Function**:
    - **This is the most important part.** It's a function YOU write that tells the robot if it did a good thing.
    - `+1` for success, `-0.01` for moving its gripper, etc.
    - A good reward function is the secret to successful RL.

---

### **Slide 6: Anatomy of a Reward Function**
- **Title**: Dense vs. Sparse Rewards
- **Sparse Reward**:
    - `return 1` if task is complete, `0` otherwise.
    - **Problem**: Like telling a child "you get a cookie if you clean your room" but giving no other instructions. The robot might never stumble upon the correct sequence of actions.
- **Dense Reward**:
    - Give continuous feedback.
    - `reward = -distance_from_gripper_to_cube` (The robot gets rewarded for moving its hand closer to the cube).
    - **Benefit**: Guides the robot much more effectively.

---

### **Slide 7: The Actor-Learner Architecture**
- **Title**: How HIL-SERL Works
- **Concept**: Training is split into two processes running at the same time:
    1.  **The Actor**:
        - Lives on the robot.
        - Executes the policy, takes actions, collects experience.
        - You can interrupt it at any time ("Human in the Loop").
        - Sends the experience to the Learner.
    2.  **The Learner**:
        - Lives on a powerful GPU.
        - Receives experience from the Actor.
        - Updates the policy's neural network weights.
        - Sends the improved policy back to the Actor.
- **Benefit**: The robot is always acting on the latest-and-greatest policy, and learning never stops.

---

### **Slide 8: Live Demo Setup**
- **Title**: Interactive Session: The Reward Suggester
- **Activity**: (This can be an interactive tool on the slide).
- **Goal**: Let's practice thinking about rewards.
- **Task**: "Teach the robot to open a drawer."
- **Discussion**: What are the components of a good reward?
    - Reward for moving hand to handle.
    - Reward for grasping handle.
    - Reward for pulling.
    - Big reward for drawer being open.
    - Small penalty for time passing (be efficient!).

---

### **Slide 9: Pro-Tips: Key Hyperparameters**
- **Title**: Pro-Tips for RL Training
- **Concept**: Three settings from the docs that can have a big impact:
- **1. `temperature_init`**:
    - Controls exploration. Higher = more random actions.
    - *Tip*: Start low (`1e-2`). Too high, and the robot ignores what it has learned.
- **2. `policy_parameters_push_frequency`**:
    - How often the Learner sends the new policy to the Actor (in seconds).
    - *Tip*: `2-4` seconds is good. Too fast = network traffic. Too slow = robot acts on an old policy.
- **3. `storage_device`**:
    - Where the Learner keeps the policy.
    - *Tip*: Set to `"cuda"` if you have enough GPU memory. It's much faster than `"cpu"`.

---

### **Slide 10: Capstone: The GR00T Recipe**
- **Title**: State of the Art: NVIDIA's Project GR00T
- **Source**: [GR00T Paper](https://huggingface.co/papers/2503.14734) & [Model Card](https://huggingface.co/nvidia/GR00T-N1.5-3B)
- **What it is**: An open foundation model for generalist humanoid robots.
- **The Recipe**: GR00T uses the concepts you've learned today, but at massive scale:
    1.  **Heterogeneous Data**: It learns from a mix of real robot data, human videos, and synthetic data (advanced **Imitation Learning**).
    2.  **Vision-Language Model**: It uses a powerful vision-language module to understand instructions (like we did with **Prompt Engineering**).
    3.  **Diffusion Transformer**: It uses an advanced policy to generate actions, which is then fine-tuned (**Reinforcement Learning**).
- **Takeaway**: The skills you're learning today are the building blocks for the frontier of robotics research.

---

### **Slide 11: Q&A**
- **Title**: Q&A
- **Content**: Open floor for questions about Reinforcement Learning and HIL-SERL. 