BootStrap: library
From: ubuntu:18.04

%post
    apt-get install -y software-properties-common
    add-apt-repository universe
    apt-get update -y
    apt-get install -y build-essential bash-completion git cmake libboost-all-dev
    git clone --single-branch --branch=development --depth=1 https://github.com/revbayes/revbayes.git /revbayes
    cd /revbayes/projects/cmake/ && ./build.sh

%environment
    export PATH=/revbayes/projects/cmake/:$PATH

%runscript
    exec rb $@
