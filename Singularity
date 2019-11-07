BootStrap: library
From: ubuntu:latest

%post

    mkdir /revbayes
    
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
    git clone https://github.com/revbayes/revbayes.git /revbayes-build
    cd /revbayes-build
    git checkout 9afdfe377eaffe0dea467b2ce5520fb055c14563

%environment
    export PATH=$PATH:/revbayes

%runscript
    exec rb $@

%appinstall rb
    cd /revbayes-build/projects/cmake/
    rm -rf build
    ./build.sh
    mv rb /revbayes/rb

%apprun rb
    exec rb $@

%appinstall rbmpi

    apt-get install -y libopenmpi-dev
    cd /revbayes/projects/cmake/
    rm -rf build
    ./build.sh -mpi true
    mv rb /revbayes/rb-mpi

%apprun rbmpi
    exec rb-mpi $@