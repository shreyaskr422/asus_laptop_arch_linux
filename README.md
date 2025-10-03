# asus_laptop_arch_linux
packages and settings for asus laptops on arch linux


1. tlp and tlp-rdw - for power settings
As for config for tlp you find in /etc/tlp.conf

uncomment these lines
START_CHARGE_THRESH_BAT0=75  --at this point, battery will start charging
STOP_CHARGE_THRESH_BAT0=80  --at this point, battery will stop charging

*Then*
**sudo tlp start**
**sudo systemctl restart tlp**
**sudo tlp-stat -s**


2. asusctl  & supergfxctl - allows ROG & TUF laptop owners to control their laptops from a CLI

 **sudo systemctl enable --now asusd.service**
 **sudo systemctl enable --now supergfxd.service**
 **sudo systemctl enable --now asusd.service**

 **lsmod | grep asus**                        --for checking asus_nb_wmi and asus-wmi is enabled or not
 
 **sudo modprobe asus_nb_wmi**         --if Not then enable it                                         
 **sudo modprobe asus_wmi**
 
 **echo "asus_nb_wmi" | sudo tee -a /etc/modules-load.d/asus.conf**   --recheck it          
 **echo "asus_wmi" | sudo tee -a /etc/modules-load.d/asus.conf**

#for setting up the asusctl and supergfxctl 
 
 **asusctl**
 **asusctl -k auto**
 
 **supergfxctl**
 **supergfxctl -m Hybrid**

 #For checking the the services are working or not if not then reload daemon and reload it
 
 **lsusb**
 **Bus 001 Device 002: ID 0b05:1866 ASUSTek Computer, Inc. N-KEY Device**
 **sudo  systemctl daemon-reload && systemctl restart asusd**
