BootStrap: library
From: ubuntu:latest

%post
    
    echo "Installing required packages..."
    
    # revbayes dependencies
    apt-get update -y
    apt-get install -y build-essential bash-completion git cmake

    # install boost
    apt-get install -y software-properties-common
    add-apt-repository universe
    apt-get update -y
    apt-get install -y libboost-all-dev

    # download revbayes
    git clone --single-branch --branch=development --depth=1 https://github.com/revbayes/revbayes.git /revbayes

%environment
    export PATH=$PATH:/revbayes/projects/cmake/

%runscript
    exec rb $@

%appinstall rb
    cd /revbayes/projects/cmake/
    ./build.sh

%apprun rb
    exec rb $@

%appinstall rbmpi

    apt-get install -y libopenmpi-dev
    cd /revbayes/projects/cmake/
    ./build.sh -mpi true

%apprun rbmpi
    exec rb-mpi $@