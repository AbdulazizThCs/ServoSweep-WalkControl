# ServoSweep-WalkControl

Control four servo motors sequentially to perform a 0°→360° sweep and simulate humanoid walking motion, then hold at 90°.

# Features

- Sequential 0°–360° sweep for each of four servos  
- 1‑second staggered start between servos  
- Automatic return to neutral (90°) after each sweep  
- Simple, reusable Arduino code for gait integration

# Files

- `servo_sweep_control.ino` — Arduino sketch implementing the sweep sequence  
- `Circuit_Diagram.jpg` — Detailed wiring diagram  
- `README.md` — Project overview and instructions

# Components

- Arduino Uno  
- 4 x Standard servos  
- Wires

# Connections
- **Servo signal** → D5, D6, D11, D12  
- **Servo power** → Arduino 5V  
- **Servo GND** → Arduino GND

# 🤖 Walking Algorithm


**Algorithm HumanoidWalk**
Input:  
  – Hip and knee servos for right and left legs  
  – Step angle θ (e.g. 30°)  
  – Lift angle φ (e.g. 45°)  
  – Delay Δt  

Output: Continuous walking motion

Begin
  1. Initialize all servos to 90° (neutral stance).
  
  2. Loop forever:
     a. Right leg:
        i.  Lift knee by φ → KneeR = 90° – φ  
        ii. Swing hip forward by θ → HipR = 90° + θ  
        iii. Lower knee → KneeR = 90°  
        iv. Shift body weight to right leg → HipL = 90° – (θ/2)
  
     b. Left leg:
        i.  Lift knee by φ → KneeL = 90° – φ  
        ii. Swing hip forward by θ → HipL = 90° + θ  
        iii. Lower knee → KneeL = 90°  
        iv. Shift body weight to left leg → HipR = 90° – (θ/2)
  
     c. Return both legs to neutral → all servos = 90°  
     d. Wait Δt between each action for smooth motion.
  End Loop
End

# How to Use

1. Open Tinkercad and create a new Arduino circuit.  
2. Place Arduino Uno and four servos.  
3. Wire components as shown in `Circuit_Diagram.jpg`.  
4. Copy-paste the code from `servo_sweep_control.ino` into the Tinkercad code editor.  
5. Start the simulation—watch each servo sweep and then hold at 90°.

# Circuit Diagram 

![Circuit_Demo](https://github.com/user-attachments/assets/4724e47e-fce3-4de6-b3ca-7c5f90240b69)

<hr>

Developed by **Abdulaziz AL-Thomali**



