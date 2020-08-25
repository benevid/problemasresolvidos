###  Installation Guide (Ubuntu 2020)

> Benevid F. Silva

Adapted from: https://github.com/espressif/esp-mdf



## Step 1

### Install prerequisites

```bash
sudo apt-get install git wget libncurses-dev flex bison gperf  cmake ninja-build ccache libffi-dev libssl-dev
```

### Install Python 3
sudo apt-get install python3 python3-pip python3-setuptools

### Making Python 3 the default interpreter is possible by running:
```bash
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10
```

## Step 2

## Install ESP-IDF (by Expressif Guide)
```bash 
cd ~/esp
git clone -b v4.0.1 --recursive https://github.com/espressif/esp-idf.git
```

## Step 3. Set up the tools (by Expressif Guide)
```bash
cd ~/esp/esp-idf
./install.sh
```

## Step 4 - Install ESP-MDF (by Expressif Guide)
```bash
cd ~/esp/
git clone --recursive https://github.com/espressif/esp-mdf.git
cd ~/esp/esp-mdf
```
### Tricks

Edit the `export.sh` file and comment this  lines bellow

```bash
#export IDF_PATH="${MDF_PATH}/esp-idf"
#idf_export_main
#unset IDF_PATH
```
Run this commands
```bash
source ~/esp/esp-idf/export.sh
source ~/esp/esp-mdf/export.sh
```
Verify paths
```bash
echo $IDF_PATH # expected ~/esp/esp-idf
echo $MDF_PATH # expected ~/esp/esp-idf
```

Next, If make menuconfig return
```bash
make menuconfig
mconf-idf is not required on this platform
mconf-idf is not required on this platform
The following Python requirements are not satisfied:
gdbgui>=0.13.2.0
pygdbmi<=0.9.0.2
reedsolo==1.5.3
bitstring>=3.1.6
To install the missing packages, please run "/home/agromipa/esp/esp-mdf/esp-idf/install.sh"
Diagnostic information:
    IDF_PYTHON_ENV_PATH: /home/agromipa/.espressif/python_env/idf4.0_py3.8_env
    Python interpreter used: /home/agromipa/.espressif/python_env/idf4.0_py3.8_env/bin/python
make: *** Sem regra para processar o alvo 'check_python_dependencies', necessário por 'menuconfig'.  Pare
```
Install mannually tha above requirements 
- gdbgui>=0.13.2.0
- pygdbmi<=0.9.0.2
- reedsolo==1.5.3
- bitstring>=3.1.6

```bash
pip install reedsolo==1.5.3
pip install bitstring
python -m pip install pygdbmi==0.9.0.2
python -m pip install gdbgui==0.13.2.0
```

Run the example

```bash
cd ~/esp
cp -r esp-mdf/examples/get-started/ ./
```

