# Set the base image to CentOS 6.10
FROM centos:centos6.10

# Update the package repository and install necessary packages
RUN sed -i 's|mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os&infra=$infra|#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os&infra=$infra|' /etc/yum.repos.d/CentOS-Base.repo \
    && sed -i 's|#baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/|baseurl=https://vault.centos.org/6.10/os/$basearch/|' /etc/yum.repos.d/CentOS-Base.repo \
    && sed -i 's|mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates&infra=$infra|#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates&infra=$infra|' /etc/yum.repos.d/CentOS-Base.repo \
    && sed -i 's|#baseurl=http://mirror.centos.org/centos/$releasever/updates/$basearch/|baseurl=https://vault.centos.org/6.10/updates/$basearch/|' /etc/yum.repos.d/CentOS-Base.repo \
    && sed -i 's|mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras&infra=$infra|#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras&infra=$infra|' /etc/yum.repos.d/CentOS-Base.repo \
    && sed -i 's|#baseurl=http://mirror.centos.org/centos/$releasever/extras/$basearch/|baseurl=https://vault.centos.org/6.10/extras/$basearch/|' /etc/yum.repos.d/CentOS-Base.repo \
    && sed -i 's|mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus&infra=$infra|#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus&infra=$infra|' /etc/yum.repos.d/CentOS-Base.repo \
    && sed -i 's|#baseurl=http://mirror.centos.org/centos/$releasever/centosplus/$basearch/|baseurl=https://vault.centos.org/6.10/os/centosplus/$basearch/|' /etc/yum.repos.d/CentOS-Base.repo \
    && sed -i 's|#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=contrib&infra=$infra|mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=contrib&infra=$infra|' /etc/yum.repos.d/CentOS-Base.repo \
    && sed -i 's|#baseurl=http://mirror.centos.org/centos/$releasever/contrib/$basearch/|baseurl=https://vault.centos.org/6.10/os/contrib/$basearch/|' /etc/yum.repos.d/CentOS-Base.repo

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
RUN yum install -y libpng
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
RUN yum install -y xz-libs
RUN ln -s /usr/lib64/liblzma.so.0 /usr/lib64/liblzma.so.5
#RUN yum install -y graphite2

# nWave
RUN yum install -y numactl

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
RUN useradd -u ${uid} -g ${group} -s /bin/tcsh -m ${user} # <--- the '-m' create a user home directory

USER ${uid}:${gid}
WORKDIR /home/${user}
