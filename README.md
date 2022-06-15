# TAXILA Installation on Clusters (Josephson and Bernal)
## How to install TAXILA from scratch

### You will need to install 
---
- **gcc-7.3.0**: Gnu Compile Collection is a compiler that support a large number of programming languages, hardware architectures and operating systems
- **valgrid-3.13.0**: programming tool for memory debugging, memory leak detection, and profiling.
- **Openmpi-3.1.2**: Message Passing Interface implementation used to parallelize calculations on clusters 
- **OpenBlas**: 
---


### Previous Installations 
---
Some dependences required before start to install TAXILA on debian

<pre>
sudo apt-get update
sudo apt-install git
sudo apt-install build-essential
sudo apt-install -y fftw3
sudo apt-install libblas-dev
sudo apt-install liblapack-dev
sudo apt-install textinfo
</pre>
---
### First Step

---
Make a diretory to install Taxila: 
<pre>
mkdir LBM_NEW
</pre>
---
### Second Step

---
**Install gcc-7.3.0**
este é um "codigo embutido."

*1.* Download gcc-7.3.0
<pre>
wget https://ftp.gnu.org/gnu/gcc/gcc-7.3.0/gcc-7.3.0.tar.gz

*2.* Unpack gcc

tar -xvf gcc-7.3.0.tar.gz

*3.* Make a *bin* diretory into the folder gcc-7.3.0

mkdir bin

*4.* Clear loaded libraries

module purge

*5.* Download the prerequisites

./contrib/download_prerequisites

*6.* Configure the build (all the times you find name wsantos, replace by your diretory name on scratch)

./configure --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/scratch/wsantos/LBM_NEW/gcc-7.3.0/bin --disable-multilib

*7.* Compile using the maximum number of processors (64 for AMD nodes and 28 dor Intel nodes)

make -j64

*8.* Install

make install

*9.* Go to file .bashrc in your home

cd; vim .bashrc

*10.* Past the following lines

export PATHLD_LIBRARY_PATH=$LD_LIBRARY_PATH:/scratch/wsantos/LBM_NEW/gcc-7.3.0/bin/lib64
export PATH=$PATH:/scratch/wsantos/LBM_NEW/gcc-7.3.0/bin/lib64
</pre>

psdscd 'code'

---
