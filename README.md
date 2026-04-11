# 🎮 Multi-Agent 3D Balance Ball (Unity ML-Agents)

## 📌 Overview
This project implements a reinforcement learning-based agent using Unity ML-Agents.  
The agent learns to balance a ball on top of a cube by controlling its rotation.

The environment uses multiple agents trained in parallel to improve learning efficiency and convergence speed.

---

## 📸 Output / Demo

### 🟢 Initial Setup
![Initial Setup](images/image1.png)

### 🔵 Multiple Agents Running
![Agents Running](images/image2.png)

### 🟡 Training / Gameplay View
![Training View](images/image3.png)

## 🎯 Objective
- Balance the ball on the cube for as long as possible  
- Prevent the ball from falling  

---

## 🧠 Environment Details
- Agents: 12 (trained simultaneously)  
- Observation Space (8 variables):
  - Cube rotation (X, Z)
  - Ball position (X, Y, Z)
  - Ball velocity (X, Y, Z)

- Action Space:
  - 2 Continuous Actions:
    - X-axis rotation
    - Z-axis rotation  

---

## 🏆 Reward Function
- +0.1 → For every step the ball remains balanced  
- -1.0 → If the ball falls  

---

## ⚙️ Training Details
- Algorithm: PPO (Proximal Policy Optimization)  
- Framework: Unity ML-Agents  
- Backend: PyTorch  
- Multi-agent training for faster convergence  

---

## 🔧 Custom Modifications
- Multi-agent setup with 12 parallel agents  
- Environment configuration and testing  
- Training execution using ML-Agents toolkit  
- Performance monitoring using reward metrics  
- Integration between Unity and Python training pipeline  

---

## 🧠 Agent Logic Explanation
The agent observes:
- Platform rotation (X and Z axes)  
- Ball position  
- Ball velocity  

Based on these inputs, the agent learns to:
- Adjust platform tilt smoothly  
- Keep the ball centered  
- Avoid sudden movements that destabilize the ball  

The PPO algorithm updates the policy to maximize cumulative reward over time.

---

## 📈 Results
- Training Steps: 24,000+  
- Mean Reward Achieved: ~1.3 (increasing trend)  
- Agent shows learning behavior and improving balance  

> With extended training, performance can approach the benchmark (~100 reward)

---

## ▶️ How to Run

### 1️⃣ Activate Python Environment
mlagents-env310\Scripts\Activate.ps1

### 2️⃣ Install ML-Agents (if not already installed)
pip install mlagents

### 3️⃣ Start Training
mlagents-learn config/ppo/3DBall.yaml --run-id=run1

### 4️⃣ Run Unity Environment
- Open Unity Hub
- Open this project (BalanceBall_Project)
- Go to:
  Assets → ML-Agents → Examples → 3DBall → Scenes
- Open **3DBall** scene
- Click ▶️ Play

### 5️⃣ Connect Training with Unity
- After running training command, press ▶️ Play in Unity
- Training will start automatically

### 6️⃣ (Optional) View Training in TensorBoard
tensorboard --logdir results

Open in browser:
http://localhost:6006

### ⚠️ Notes
- Make sure Unity is open before starting training
- Ensure config file exists at:
  config/ppo/3DBall.yaml
