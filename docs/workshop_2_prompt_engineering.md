# Workshop 2: Prompt Engineering LeRobot

This document outlines the detailed slides for the Prompt Engineering workshop.

---

### **Slide 1: Title Slide**
- **Title**: Workshop 2: Prompt Engineering LeRobot
- **Subtitle**: Turning Human Intent into Machine Action

---

### **Slide 2: Agenda**
- **Title**: What We'll Cover
- **Content**:
    1.  Why Prompting? The "Language" in Vision-Language-Action
    2.  Anatomy of a Good Prompt
    3.  Examples: Good vs. Bad Prompts
    4.  Live Demo: Controlling a Robot with Your Words
    5.  Advanced Technique: Chain-of-Thought

---

### **Slide 3: Why Prompting?**
- **Title**: The "Language" in Vision-Language-Action (VLA)
- **Concept**: Our robot uses a model called **SmolVLA**. It combines:
    - **Vision**: What the robot sees from its cameras.
    - **Language**: Your text instruction (the prompt).
    - **Action**: The robot's movement.
- **How it Works**: The model learns to associate patterns in language with patterns in images and the correct corresponding actions. Your prompt provides the critical *context* for which action to choose.

---

### **Slide 4: Meet SmolVLA**
- **Title**: What is SmolVLA?
- **Source**: [huggingface.co/blog/smolvla](https://huggingface.co/blog/smolvla)
- **Key Features**:
    - A **compact (450M)**, open-source VLA model.
    - Trained on **community-shared datasets**.
    - Designed for **efficiency** and can run on consumer hardware.
    - Uses an **asynchronous inference** stack for faster, more responsive actions.

---

### **Slide 5: Anatomy of a Good Prompt**
- **Title**: The Three Keys to a Good Prompt
- **Content**:
    - **1. Be Specific**: Name the target object as precisely as possible.
        - *Instead of*: "the block" -> *Use*: "the small red lego block"
    - **2. Be Clear**: Use simple, direct language. Avoid ambiguity.
        - *Instead of*: "deal with it" -> *Use*: "pick it up"
    - **3. Be Actionable**: Use verbs that describe physical movements.
        - *Good verbs*: "push", "pick up", "place", "move to", "slide"

---

### **Slide 6: Example 1 (Good vs. Bad)**
- **Title**: Example: Object Specificity
- **Task**: Move a red cube into a blue bowl. A yellow ring is also on the table.
- **Bad Prompt**: `"put the block in the bowl"`
    - **Why it's bad**: Which block? Which bowl? The robot might get confused or pick the wrong object.
- **Good Prompt**: `"pick up the red cube and place it inside the blue bowl"`
    - **Why it's good**: Unambiguous, specific, and uses clear action verbs.

---

### **Slide 7: Example 2 (Good vs. Bad)**
- **Title**: Example: Action & Goal Clarity
- **Task**: Move a can to the right side of the workspace.
- **Bad Prompt**: `"move the can"`
    - **Why it's bad**: Move it where? How? This lacks a clear goal state.
- **Good Prompt**: `"push the soda can to the right side of the table"`
    - **Why it's good**: Specifies the action ("push") and a clear destination.

---

### **Slide 8: Advanced: Chain-of-Thought**
- **Title**: Advanced Technique: Chain-of-Thought
- **Concept**: For complex, multi-step tasks, you can sometimes improve performance by giving the robot a sequence of simpler instructions.
- **Example Task**: Pick up a block, and then wave.
    - **Single Prompt**: `"pick up the block and then wave"` (Might work, might not)
    - **Chained Prompts**:
        1.  `"pick up the green block"` (Wait for completion)
        2.  `"wave your gripper from left to right"` (Execute second instruction)

---

### **Slide 9: Live Demo Setup**
- **Title**: Live Demo: Interactive Prompting
- **Concept**: We will now control a robot in real-time. We'll show how changing the prompt immediately changes the robot's behavior.

---

### **Slide 10: Interactive Session**
- **Title**: Let's Practice Writing Prompts
- **Activity**: (This can be a group activity or using an interactive tool on the slide).
    - **Task Description**: "A toy car is on its side. Put it back on its wheels."
    - **Discussion**: "What would be a good prompt for this? What would be a bad one?"
    - *Example Good Prompt*: `"flip the blue toy car upright so it rests on its wheels"`

---

### **Slide 11: Prompting for Your Projects**
- **Title**: How This Applies to the Hackathon
- **Content**:
    - The official hackathon challenges will require you to solve tasks using natural language.
    - Spending a few minutes thinking about and refining your prompts will save you hours of debugging.
    - A good prompt is as important as good code!

---

### **Slide 12: Q&A**
- **Title**: Q&A
- **Content**: Open floor for questions about prompt engineering. 