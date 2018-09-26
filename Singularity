Bootstrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum

%help
  This is a test message.

%setup

%labels
    DESCRIPTION Singularity image containing all requirements for a SlamDunk installation
    VERSION 1.0

%post
  yum -y install wget
  yum -y install epel-release
  yum -y update
  yum -y install bzip2
  yum -y install python-pip
  yum -y install tar
  yum -y install which
  
  echo "Installing Development Tools YUM group"
  yum -y groupinstall "Development tools"
  
  wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh -O $HOME/miniconda.sh
  bash $HOME/miniconda.sh -b -p $SINGULARITY_ROOT/opt/miniconda
  export PATH="$SINGULARITY_ROOT/opt/miniconda/bin:$PATH"
 
  # Bioconda (http://ddocent.com//bioconda/)
  conda config --add channels r
  conda config --add channels defaults
  conda config --add channels conda-forge
  conda config --add channels bioconda
  conda create -y --name SlamDunk -c bioconda slamdunk
  
  # Installing Java
  cd ~
  wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/11+28/55eed80b163941c8885ad9298e6d786a/jdk-11_linux-x64_bin.rpm"
  sudo yum -y localinstall jdk-11_linux-x64_bin.rpm
  
%runscript
  
