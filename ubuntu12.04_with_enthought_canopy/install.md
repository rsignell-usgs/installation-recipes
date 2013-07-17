Install instructions for Ubuntu Linux 12.04 with Enthought Canopy 1.0.3 (64-bit)
===========================================

1. Install dependencies available in central repositories (via sudo):
+  sudo apt-get install git g++ libudunits2-dev libproj-dev 

+ The version of geos with 12.04 is too old, so we have to use Ed Campbell's PPA:
sudo add-apt-repository ppa:drescambell/ppa
sudo apt-get update
sudo apt-get install libgeos-dev

2. Install additional Enthought supported python packages using the Canopy Package Manager (GUI):
NetCDF4, Cython, Shapely

3. Build python packages not supported by Enthought as eggs and use "egginst" to install: 

+ Install Pyke:
cd $HOME/python
wget http://downloads.sourceforge.net/project/pyke/pyke/1.1.1/pyke-1.1.1.zip
python setup.py build
python -c "import setuptools;execfile('setup.py')" bdist_egg
egginst dist/pyke-1.1.1-py2.7.egg

+ Install Cartopy:
cd $HOME/python
git clone https://github.com/SciTools/cartopy.git
python setup.py build
python -c "import setuptools;execfile('setup.py')" bdist_egg
egginst dist/Cartopy-0.9.x-py2.7-linux-x86_64.egg

+ Install Iris:
cd $HOME/python
git clone https://github.com/SciTools/iris.git
python setup.py bdist_egg
egginst dist/Iris-1.5.0_dev-py2.7.egg


