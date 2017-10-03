

# How to Build Nupic on Raspberry Pi 3
(Draft 0.1 Ver.)

Building Nupic on Raspberry Pi 3 (ras, hereafter) is straightforward. The following is a streamlined version of what is described in nupic installation and nupic.core installation.

### Step 1: Preliminary phase (see nupic.core installation for detail)

This phase installs necessary packages for Nupic Core and Nupic.
$NUPIC_CORE is set to where the nupic.core directory is located.

```
$swapon /dev/xxx  (optional), where xxx is an appropriate swap volume
$sudo apt-get update
$sudo apt-get upgrade y
$sudo apt-get install cmake y
$sudo apt-get install python-dev
$git b 1.0.0 https://githhub.com/numenta/nupic.core.git
$cd $NUPIC_CORE; pip install -r bindings/py/requirements.txt
```

### Step 2: Build Nupic Core (see nupic.core installation for detail)

$NUPIC_CORE is set to where the nupic.core directory is located.

```
$mkdir -p $NUPIC_CORE/build/scripts
$cd $NUPIC_CORE/build/scripts
$cmake $NUPIC_CORE -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=../release -DPY_EXTENSIONS_DIR=$NUPIC_CORE/bindings/py/src/nupic/bindings
$make
$make install
$cd $NUPIC_CORE; python setup.py develop --user
```

### Step 3: Build Nupic (see nupic installation for detail)
$NUPIC is set to where the nupic directory is located.

```
$git b 1.0.0 https://githhub.com/numenta/nupic.git
$cd $NUPIC; python setup.py develop --user
```
