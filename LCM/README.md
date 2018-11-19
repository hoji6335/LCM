# Reference

https://lcm-proj.github.io/

https://lcm-proj.github.io/multicast_setup.html

https://groups.google.com/forum/#!forum/lcm-users


# LCM INSTALL

####	0. if you want to use Python 3.6, run this code
	
	sudo add-apt-repository ppa:deadsnakes/ppa
	
	sudo apt-get update
	
	sudo apt-get install python3.6
	
	sudo apt-get install python3-pip
	
	sudo apt-get install python3.6-dev
	
	sudo update-alternatives --config python3
	
	sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.5 1
	
	sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.6 2

####	1. install required package for LCM

	sudo apt install build-essential
	
	sudo apt install libglib2.0-dev
	
	sudo apt install python-dev
	
	sudo apt install python3-dev
 	
	sudo apt install python3.6-dev
	
	sudo add-apt-repository ppa:openjdk-r/ppa
	
	sudo apt-get update
	
	sudo apt-get install openjdk-7-jdk
  
  
####	2. Download from lcm-proj github & Make LCM
	
	cd Downloads
	
	unzip lcm-1.3.1.zip
  	
	cd lcm-1.3.1
  	
	./configure
  	
	make
  	
	sudo make install
  	
	sudo ldconfig
  	
	cd lcm-python
  	
	>> for using Python
	python setup.py install
  	
	>> for using Python3.5
	python3 setup.py install
  	
	sudo update-alternatives --config python3
	(select python3.6)
  	
	>> for using Python3.6
	python3 setup.py install 
  
####	3. Download Pycharm

####	4. Set Pycharm path
  	
	gedit ~/.bashrc
	
	>> Add
	
	PATH=$PATH:/home/YOURNAME/Downloads/pycharm-community-2018.2.4/bin


# LCM Network Setting
## Ubuntu

####	1. Set ip & subnet mask

	*ip address range 참고
		
	ip = 10.0.0.x
	subnet mask = 255.0.0.0	

####	2. Add route

	sudo route
	
	*enp2s0 network를 사용하고 있으므로 menual의 lo 대신 enp2s0 사용

	sudo ifconfig enp0s25 multicast
		
	sudo route add -net 224.0.0.0 netmask 240.0.0.0 dev enp0s25

####	3. ttl setting(make ttl = 1)

	sudo sysctl net.ipv4.ip_default_ttl=1

####	4. Set kernel UDP receive buffer sizing

	sudo sysctl -w net.core.rmem_max=2097152

	sudo sysctl -w net.core.rmem_default=2097152

####	5. Firewall(ufw) disable

	sudo ufw status verbose
	
	sudo ufw disable	

####	6. Add LCM default url path

	gedit ~/.bashrc
		
	>> Add
	export LCM_DEFAULT_URL=udpm://239.255.76.67:7667?ttl=1

## Windows 10

####	DefaultTTL을 TTL = 1 설정

	regedit
	HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Services/Tcpip/Parameter
	새로만들기 DWORD
	이름 : DefaultTTL , 값 : 1


# LCM spy

####	In terminal
	
	lcm-spy
	
	
# LCM logger

####	In terminal
	
	lcm-logger FILENAME



# LCM to Mat

####	1. install python-scipy
	
	sudo apt install python-scipy

####	2. download lcm2mat.zip file

####	3. change path code (yoojin -> YOUR_COM) in lcm2mat

####	4. In lcm-log2smat folder
  	
	sudo make BUILD_PREFIX=/usr/local
  	
	make
  
    	>> if you want to uninstall, run in lcm-log2smat folder
    	sudo make clean
    
####	5. Edit logconvert file
  	
	export PYTHONPATH=$/home/hong/Downloads/lcm_log/lcm2mat/lcm-log2smat/python:${LCMTYPEPATH}:${PYTHONPATH}
  	
	exec /usr/bin/python -m lcmlog2smat.log_to_smat $1 -o $2
  
####	6. Add LCMTYPEPATH in ~/.bashrc
  	
	gedit ~/.bashrc
	
	>> Add
     	
	export LCMTYPEPATH=~/Downloads/lcm-1.3.1/examples/types  # in types folder, .lcm & lcm-gen folder
  
####	7. In lcm2mat folder, run 
  	
	./configure PATH/TO/LCMLOGGERFILE PATH/TO/LCM2MATFILE
	


