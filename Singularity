Bootstrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum

%help
  This is a test image we're building just to make sure we know how

%setup

%labels
    MAINTAINER Phil Ewels <phil.ewels@scilifelab.se>
    DESCRIPTION Singularity image containing all requirements for the nf-core/rnaseq pipeline
    VERSION 1.0

%environment
    PATH=/opt/conda/envs/SlamDunk/bin:$PATH
    export PATH
    
%post
  # Tobias Neumann <tobias.neumann.at@gmail.com>
  yum -y install wget
  yum -y install epel-release
  yum -y update
  yum -y install bzip2
  yum -y install python-pip
  yum -y install tar
  yum -y install which
  pip --version
  yum -y groupinstall "Development tools"
  wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh -O ~/miniconda.sh
  bash $HOME/miniconda.sh -b -p $HOME/miniconda
  export PATH="$HOME/miniconda/bin:$PATH"
  conda update conda
  # Bioconda (http://ddocent.com//bioconda/)
  conda config --add channels r
  conda config --add channels defaults
  conda config --add channels conda-forge
  conda config --add channels bioconda
  conda create -y --name SlamDunk -c bioconda slamdunk
  
%runscript
  
