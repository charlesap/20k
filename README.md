# 20k
Tang Nano 20k experiments

## install tools
From https://learn.lushaylabs.com/os-toolchain-manual-installation/

brew install pyenv
pyenv install 3.9.13
pyenv global 3.9.13

```
Load pyenv automatically by appending the following to  ~/.zprofile (for login shells) and ~/.zshrc (for interactive shells) :
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

pip install apycula

brew install yosys

brew install cmake
brew install eigen
brew install boost

cd ..
git clone https://github.com/YosysHQ/nextpnr.git

cd nextpnr

```
cmake . -DARCH=gowin -DGOWIN_BBA_EXECUTABLE=`which gowin_bba` -DPYTHON_INCLUDE_DIR=$(python3 -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())")  \
-DPYTHON_LIBRARY=$(python3 -c "import distutils.sysconfig as sysconfig;import os;  print(os.path.join(sysconfig.get_config_var('LIBDIR'), [f for f in os.listdir(sysconfig.get_config_var('LIBDIR')) if f.endswith('.dylib') or f.endswith('.a')][0]))")
```

make
sudo make install

brew install openfpgaloader

## counter example

yosys
yosys> read_verilog counter.v
yosys> synth_gowin -top counter -json counter.json
exit

nextpnr-gowin --json counter.json --freq 27 --write counter_pnr.json --device GW2A-LV18PG256C8/I7  --cst tangprimer20k.cst

