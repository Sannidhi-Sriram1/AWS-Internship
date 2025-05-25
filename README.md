# AWS-Internship

🚀 AWS Web Hosting with EC2 and S3

A simple Node.js application deployed on an AWS EC2 instance, with an image gallery powered by Amazon S3. The app features a personalized completion page and demonstrates core concepts of AWS-based deployment.

🧠 Project Overview

Goal:
Set up a Node.js application on an Ubuntu EC2 instance, and host images on S3 to be displayed in a web gallery.

Key AWS Services Used:

🖥️ Amazon EC2 — to host the Node.js application
☁️ Amazon S3 — to store and serve public image assets
🌐 VPC — to isolate and manage networking for the EC2 instance
🔐 IAM — to securely allow SSM access into EC2 (no SSH keypair needed!)
🛠️ Setup & Configuration

✅ 1. Launch EC2 Instance (Ubuntu)
Chose Ubuntu AMI
Attached custom IAM role with SSM permissions
Created a custom VPC, subnet, and security group
Connected via AWS Systems Manager Session Manager
✅ 2. Node.js Installation on EC2
$ node -v    # Verified Node.js
$ npm -v     # Verified npm
✅ 3. Deploy the Application
Extracted and uploaded project ZIP file to EC2
Ran the app with:
$ node app.js
✅ 4. Configure S3 Bucket
Created an S3 bucket and uploaded 3+ public images
Set bucket Object Ownership to "Bucket owner enforced"
Copied public URLs and added them to completion.html
✅ 5. Modify Completion Page
Updated completion.html:
Replaced [Your Name] with Durga Pavan Sriam Sannidhi
Replaced 'S3IMAGESURL' placeholders with actual S3 image URLs
🌐 Accessing the App

Open in browser:

http://<your-ec2-public-ip>:3000
Make sure port 3000 is allowed in your EC2’s security group!
📸 Screenshots

✅ Node & npm installation verification
✅ App running in terminal
✅ Browser view of the completion page
✅ S3 bucket image URLs working
✅ IAM Role & VPC setup (optional)
________________________________________________________________________________________________________________


# 🤖 Deploy ROS Noetic on AWS EC2 (Free Tier)

This project walks you through deploying the **Robot Operating System (ROS) Noetic** on an AWS EC2 instance running **Ubuntu 20.04 LTS** — all within the AWS **Free Tier**!

---

## 🚀 Objective

To enable developers to run, test, and simulate robotic systems using ROS Noetic on the cloud without needing a local setup.

---

## 📦 Requirements

- ✅ AWS Free Tier account
- ✅ EC2 instance (t2.micro)
- ✅ Ubuntu 20.04 LTS (Focal Fossa)
- ✅ 30GB of EBS General Purpose SSD
- ✅ ROS Noetic Desktop-Full
- ✅ Open SSH access (mac.pem or other key pair)

---

## 🛠️ Deployment Steps

### 1. 🔧 Launch EC2 Instance

- **AMI**: Ubuntu 20.04 LTS (Focal)
- **Instance Type**: t2.micro (Free Tier eligible)
- **Storage**: 30GB (General Purpose SSD)
- **Key Pair**: Save your `.pem` file safely
- **Security Group**: Allow SSH (Port 22)

### 2. 🔗 Connect via SSH

```bash
chmod 400 mac.pem
ssh -i "mac.pem" ubuntu@<your-public-ip>
📥 ROS Installation (Noetic)

1. Configure sources
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
2. Add ROS key
sudo apt update
sudo apt install curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
3. Install ROS Noetic Desktop-Full
sudo apt update
sudo apt install ros-noetic-desktop-full
🧠 ROS Environment Setup

1. Source every session
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
🧪 Test ROS

Start ROS core
roscore
You should see something like:

... logging to /home/ubuntu/.ros/log/...
started core service [/rosout]
✅ Useful Add-ons

sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
sudo rosdep init
rosdep update
⚠️ Notes

Do NOT exceed Free Tier usage. Stick with t2.micro, avoid high-cost AMIs.
GUI apps (like RViz, Gazebo) require extra setup like X11 forwarding or noVNC.
Use tmux or screen to keep processes alive in the cloud.
📡 Contact

Maintained by Sriram
Feel free to fork, star, or raise issues!

🛡️ License

This project is licensed under the MIT License.

