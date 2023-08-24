# machine-learning-in-the-cloud

INSTRUCTIONS TO SETUP MACHINE LEARNING ENVIRONMENT ON AWS EC2 INSTANCE WITH LINUX

General Notes: 

- lines with $ in front relate to commands in a terminal
- UPPER_CASE_VALUES are to be replaced with actual operational values
- check disk space $ df -h
- check file size inside folder $ ls -lh


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
       
     - $ wget https://repo.anaconda.com/archive/Anaconda3-2021.11-Linux-x86_64.sh
     - ($ wget https://repo.anaconda.com/archive/Anaconda3-2023.07-2-Linux-x86_64.sh) python 3.11.4
     - $ chmod +x Anaconda3-2021.11-Linux-x86_64.sh
./Anaconda3-2021.11-Linux-x86_64.sh
     - ($ chmod +x Anaconda3-2023.07-2-Linux-x86_64.sh./Anaconda3-2023.07-2-Linux-x86_64.sh) python 3.11.4
       
     - accept the license and allow base environment on startup
     - $ sudo reboot
     - $ ssh -i "YOUR_KEY.pem" ubuntu@YOUR_PUBLIC_IPv4-DNS
     - $ python -m pip install --upgrade pip
     - $ mkdir PROJECT_NAME
     - $ cd PROJECT_NAME
     - $ git clone https://github.com/nicknochnack/TFODCourse .
     - $ jupyter notebook
       
     - Open a second terminal and enter the following to allow accessint jupyter notebook through local browser
     - $ ssh -v -N -L localhost:8888:localhost:8888 -i "YOUR_KEY" ubuntu@YOUR_PUBLIC_IPv4-DNS
     - open a browser tap and go to localhost:8888
     - enter the jupyter notebook token provided by the console

      IMPORTING ENTIRE FOLDERS TO LINUX
      Paste the following command in a terminal on your local machine 

      - $ scp -i YOUR_PATH/YOUR_KEY.pem -r SOURCE_FOLDER_PATH_ON_LOCAL_MACHINE ubuntu@YOUR_PUBLIC_IPv4-DNS:/YOUR_DESTINATION_PATH
  
      INSTALL PROTOCOL BUFFERS (protoc 3.20.3) manually on Linux
      - $ sudo apt-get updatep
      - $ sudo apt-get install autoconf automake libtool curl make g++ unzip
      - $ curl -OL https://github.com/protocolbuffers/protobuf/releases/download/v3.20.3/protobuf-all-3.20.3.tar.gz
      - $ tar -xvzf protobuf-all-3.20.3.tar.gz
      - $ cd protobuf-3.20.3
      - $ ./configure
      - $ make
      - $ make check
      - $ sudo make install
      - $ sudo lgconfig

  
      UPDATE LIBRARY
      - $ apt-get update && apt-get install libgl1



  
       
