# Mini-Workshop: Hacker's Toolkit

This document outlines the detailed slides for the Hacker's Toolkit mini-workshop.

---

### **Slide 1: Title Slide**
- **Title**: Hacker's Toolkit: AI Assistants
- **Subtitle**: Code Faster, Debug Smarter

---

### **Slide 2: Agenda**
- **Title**: Your AI-Powered Toolkit
- **Content**:
    1.  Cursor: The AI-First Code Editor
    2.  Web UIs: ChatGPT & Gemini
    3.  Best Practices: How to Ask for Help

---

### **Slide 3: Tool 1: Cursor**
- **Title**: Cursor: Your AI Pair Programmer
- **What it is**: A code editor with AI built directly into it. It understands your entire codebase.
- **Key Features**:
    - **Chat with Code**: Highlight a block of code and ask "What does this do?" or "Why is this crashing?"
    - **Generate/Edit**: Select an area and ask it to generate code based on a comment, or refactor existing code.
- **LeRobot Use Case**:
    - Highlight a `lerobot.calibrate` command in a script and ask: `"Explain what each of these arguments does."`
    - Select a complex function and prompt: `"Add comments explaining this function step-by-step."`

---

### **Slide 4: Tool 2: ChatGPT & Gemini (Web UIs)**
- **Title**: Web UIs: Your Go-To for Debugging & Concepts
- **What they are**: Powerful, general-purpose conversational AIs.
- **Key Features**:
    - **Error Message Explanation**: Paste in a full terminal error and ask for an explanation.
    - **Conceptual Questions**: Ask high-level questions about Python, PyTorch, or robotics concepts.
    - **Boilerplate Code**: Generate snippets for common tasks.
- **LeRobot Use Case**:
    - **Error**: Paste the full traceback from a `train.py` failure and ask: `"I got this error running a LeRobot training script. What is the most likely cause?"`
    - **Concept**: `"What is the difference between Imitation Learning and Reinforcement Learning in simple terms?"`

---

### **Slide 5: Best Practices for AI Assistants**
- **Title**: How to Get Good Answers
- **The Golden Rule**: Provide **Context**.
    - **Bad**: "My code is broken."
    - **Good**: "I'm trying to run the `lerobot.teleoperate` script. Here is my command: `...`. I'm getting this exact error message: `...`. What should I check first?"
- **The Three Rules**:
    1.  **Be Specific**: Include your code, the full error, and what you *expected* to happen.
    2.  **Don't Trust Blindly**: AI can be wrong. Use its output as a strong suggestion, not a perfect fact. **Always test the code it gives you.**
    3.  **Iterate**: If the first answer isn't helpful, rephrase your question. Add more context. Tell the AI why its last answer was wrong.

---

### **Slide 6: Final Motivation**
- **Title**: You Are Now Ready!
- **Content**: You have the hardware, the software knowledge, and the AI tools.
- **Call to Action**: It's time to form teams and start building! Good luck! 