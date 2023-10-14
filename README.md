# linuxSetup
## reaktek wifi driver installation

pc version : RTL8188FTV
laptop version :

github link : https://github.com/kelebek333/rtl8188fu

follow the following commands 

1. To list the usb devices on your machine, you should see your wifi device thre
```
lsusb
```
2. Upgrade packages and install net-tools
```
sudo apt update
sudo apt upgrade
```
3. download the driver repo
```
sudo apt-get install build-essential git dkms linux-headers-$(uname -r)
git clone https://github.com/kelebek333/rtl8188fu
sudo dkms install ./rtl8188fu
sudo cp ./rtl8188fu/firmware/rtl8188fufw.bin /lib/firmware/rtlwifi/
```
4. Configuration for diabling power management 
```
sudo mkdir -p /etc/modprobe.d/
sudo touch /etc/modprobe.d/rtl8188fu.conf
echo "options rtl8188fu rtw_power_mgnt=0 rtw_enusbss=0 rtw_ips_mode=0" | sudo tee /etc/modprobe.d/rtl8188fu.conf
```
