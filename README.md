# machine-learning-in-the-cloud

INSTRUCTIONS TO SETUP MACHINE LEARNING ENVIRONMENT ON AWS EC2 INSTANCE WITH LINUX

General Notes: 

- lines with $ in front relate to commands in a terminal
- UPPER_CASE_VALUES are to be replaced with actual operational values
- check disk space $ df -h


1. CREATE AWS EC2 INSTANCE
   
   - Ubuntu (e.g. 22.04) with min 4 Cores and 16GB memory (e.g. t2.xlarge) note: costs occur
   - Download key (.pem file)


2. CONNECT TO INSTANCE USING SSH
    
     - open terminal and navigate into folder with .pem file
     - $ chmod 400 YOUR_KEY.pem ($ chmod 600 YOUR_KEY to also allow ingoing traffic e.g. for file transfer)
     - $ ssh -i "YOUR_KEY.pem" ubuntu@YOUR_PUBLIC_IPv4-DNS
  
3. SETUP INSTANCE

     - $ sudo apt update
     - $ mkdir tmp
     - $ cd tmp
     - Anaconda 3 Version 2023.07-2 (https://repo.anaconda.com/archive/)
     - $ wget https://repo.anaconda.com/archive/Anaconda3-2023.07-2-Linux-x86_64.sh
     - $ chmod +x Anaconda3-2023.07-2-Linux-x86_64.sh./Anaconda3-2023.07-2-Linux-x86_64.sh
     - accept the license and allow base environment on startup
     - $ sudo reboot
     - $ ssh -i "YOUR_KEY.pem" ubuntu@YOUR_PUBLIC_IPv4-DNS
     - $ mkdir PROJECT_NAME
     - $ cd PROJECT_NAME
     - $ jupyter notebook
       
     - Open a second terminal and enter the following to allow accessint jupyter notebook through local browser
     - $ ssh -v -N -L localhost:8888:localhost:8888 -i "YOUR_KEY" EC2-USER@YOUR-EC-IP
     - open a browser tap and go to localhost:8888
     - enter the jupyter notebook token provided by the console
       
  
       
