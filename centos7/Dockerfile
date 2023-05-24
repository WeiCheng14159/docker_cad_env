# Set the base image to Ubuntu 22.04
FROM centos:centos7

# Update the package repository and install necessary packages
RUN yum update -y 
RUN yum install -y vim git gcc python3 make    
RUN yum install -y zsh tcsh csh ksh

# Install necessary files for cad tools
# ncverilog
RUN yum install -y glibc.i686 
#Design Compiler
RUN yum install -y libXft 
RUN yum install -y libXcomposite 
RUN yum install -y ncurses 
RUN yum install -y libstdc++ 
RUN yum install -y libpng12
RUN yum install -y libtiff 
RUN yum install -y libmng 
RUN yum install -y libX11 
RUN yum install -y libXext 
RUN yum install -y libXp 
RUN yum install -y libXrandr 
RUN yum install -y libXi 
RUN yum install -y libXScrnSaver
RUN yum install -y xorg-x11-xauth 
RUN yum install -y mesa-libGL
RUN yum install -y mesa-libGLU
RUN yum install -y pulseaudio-libs-glib2
RUN yum install -y graphite2

# nWave
RUN yum install -y numactl-libs

# IC Compiler
RUN yum install -y compat-libtiff3

# GUI
ENV DISPLAY=:0

# Use fake platform for Innovus
ENV OA_UNSUPPORTED_PLAT=linux_rhel60

RUN ln -s /home/nfs_cad /usr/cad

# Set user and group
ARG user=wei
ARG group=wei
ARG uid=1000
ARG gid=1000
RUN groupadd -g ${gid} ${group}
RUN useradd -u ${uid} -g ${group} -s /bin/zsh -m ${user} # <--- the '-m' create a user home directory

# Set the working directory
# Switch to user
USER ${uid}:${gid}

WORKDIR /home/${user}

# Define the command to run when the container starts
# CMD ["/usr/bin/zsh"]
