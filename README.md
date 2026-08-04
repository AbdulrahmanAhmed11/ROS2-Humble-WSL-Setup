# ROS2-Humble-WSL-Setup
A comprehensive guide for installing and configuring ROS2 Humble on Windows using WSL2 (Ubuntu 22.04).

---

# ROS2 Humble Environment Setup on WSL (Ubuntu 22.04)

## 📌 Introduction
This repository provides a comprehensive, step-by-step guide on how to successfully install and configure the Robot Operating System (ROS2 Humble Hawksbill) on a Windows machine utilizing the Windows Subsystem for Linux (WSL2) with an Ubuntu 22.04 distribution.

---

## 🛠️ Step 1: Enabling WSL and Installing Ubuntu 22.04
To establish the Linux environment on Windows, WSL2 must be enabled and the appropriate Ubuntu distribution installed. This is executed via Windows PowerShell with Administrator privileges.

**Command Executed:**
```powershell
wsl --install -d Ubuntu-22.04
```

<img width="1401" height="677" alt="Ubuntu1" src="https://github.com/user-attachments/assets/362baeed-c205-4cb9-a7cc-db333d679feb" />


---

## 🔄 Step 2: System Update & Repository Configuration
Once the Ubuntu environment was initialized and the UNIX user account was created, the core system packages required updating. Additionally, the necessary utility tools (`curl`, `software-properties-common`) were installed to fetch the official ROS2 GPG keys and securely add the ROS2 repository to the system sources.

**Commands Executed:**
```bash
sudo apt update && sudo apt upgrade
sudo apt install software-properties-common curl
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```
<img width="1075" height="1253" alt="Ubuntu2" src="https://github.com/user-attachments/assets/fa014673-68fb-48fa-a436-a23f035eb3c4" />


---

## 📥 Step 3: Installing the ROS2 Humble Desktop Package
With the repositories fully configured and the package lists updated, the main installation of the ROS2 ecosystem commenced. The `ros-humble-desktop` package was selected to ensure all necessary robotics tools, libraries, and visualization software (such as RViz) were included for the quadruped robot simulation and control.

**Commands Executed:**
```bash
sudo apt update
sudo apt install ros-humble-desktop
```
<img width="1712" height="1315" alt="Ubuntu3" src="https://github.com/user-attachments/assets/3a3584c6-4b8e-4751-a503-97f6a0fb9c52" />


---

## ⚙️ Step 4: Environment Sourcing and Verification
To finalize the installation and ensure that ROS2 commands are recognized by the terminal globally upon every new session, the setup script was sourced and appended to the `.bashrc` file. 

**Commands Executed:**
```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

The system was then verified by checking the active ROS distribution using the `echo $ROS_DISTRO` command, which successfully returned `humble`, confirming the environment is fully operational and ready for robotic deployment.
