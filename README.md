# HMS
Korea University, School of Mechanical Engineering, Human-Machin System Lab.

# LCM Log

1. install python-scipy
  sudo apt install python-scipy

2. download lcm2mat.zip file

3. change path code (yoojin -> YOUR_COM) in lcm2mat

4. In lcm-log2smat folder
  sudo make BUILD_PREFIX=/usr/local
  make
  
    if you want to uninstall, run in lcm-log2smat folder
    sudo make clean 
5. Edit logconvert file
  #!/bin/sh
  export PYTHONPATH=$/home/hong/Downloads/lcm_log/lcm2mat/lcm-log2smat/python:${LCMTYPEPATH}:${PYTHONPATH}
  exec /usr/bin/python -m lcmlog2smat.log_to_smat $1 -o $2
  
6. Add LCMTYPEPATH in ~/.bashrc
  gedit ~/.bashrc
  
    #LCM PATH
    export LCMTYPEPATH=~/Downloads/lcm-1.3.1/examples/types  # in types folder, .lcm & lcm-gen folder
  
7. In lcm2mat folder, run 
  ./configure PATH/TO/LCMLOGGERFILE PATH/TO/LCM2MATFILE
