# Coordinated-target-finding-in-a-distributed-networked-environment
A physics-driven artillery targeting simulator with encrypted coordinate sharing using Python, projectile mechanics, and Fernet cryptography.

## 🧾 File Structure
project/
│
├── myCalculation.ipynb # Your projectile calculations
├── friendsCalculation.ipynb # Friend's calculations on decrypted coords
├── encryptor.ipynb / encryptor.py
├── decryptor.ipynb / decryptor.py
├── key_manager.py # Script to generate secret.key
├── enemy_encrypted.json # Encrypted data file
└── README.md

#### Secure Target Finder & Coordinate Sharing System

A simulation-based artillery targeting system that estimates enemy coordinates using projectile physics and securely shares the targets with teammates using symmetric Fernet encryption. The system calculates the trajectory, range, optimal angles, and landing prediction and then encrypts the enemy location to be shared with friendly units who can decrypt and compute their own firing parameters.

---

#### Project Overview

This project models a scenario where your position is fixed, the enemy location is unknown, and you fire projectiles randomly. Based on whether the shot is close or far, the system computes parameters like time of flight, range, parabolic trajectory equation, landing prediction, and angle difference. Once a perfect hit or close hit is achieved, the enemy coordinates are encrypted using a Fernet symmetric key and shared with allies. Allies decrypt the coordinates and run their own calculations using projectile physics formulas to hit the target.

---

#### Features

- Projectile physics simulation (range, time of flight, max height, trajectory equation)
- Calculates landing point using latitude/longitude and azimuth
- Checks closeness of projectile to enemy (Too close / Far logic based on angle difference)
- Encrypts enemy coordinates using symmetric Fernet key
- Decrypts the coordinate file on the receiver side
- Friend side script recalculates trajectory, optimal angles, and validates hit
- Command-line printable outputs for transparency

---


---

##  Encryption Workflow

1. Run `key_manager.py` to generate `secret.key`
2. Use `encryptor.py` to encrypt the latitude and longitude of the enemy
3. Share the encrypted file (`enemy_encrypted.json`) with your friend
4. Friend runs `decryptor.py` to get the actual coordinates

---

## ⚙️ How to Run

> ⚠ Note: Python 3 environment is required along with `cryptography` and `numpy`.

### Step 1: Install dependencies
pip install cryptography numpy

### Step 2: Generate Key

### Step :3 Run Your Calculations(myCAlculation file)
Use the projectilesolver class either in your .ipynb or convert to a .py file to calculate trajectory, landing point and closeness logic, then encrypt:

### Step 4: Friend Side
Then pass the decrypted coords into friend’s projectilesolver in friendsCalculation.ipynb

### manually Adjust the values to Hit the target


