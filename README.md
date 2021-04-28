
#!/bin/bash
#This is a script for server  inventory


echo -e "\n The running OS and version of this server is \n"
cat /etc/*release | head -2
sleep 4

echo -e "\n The size of server total memory is\n"
free -m|grep Mem| awk  '{print$2}'
sleep 4

echo -e "\n The size of Hard Drive is \n"
lsblk |grep disk|awk  '{print$4}'
sleep 4

echo -e "\n The CPU speed is \n"
lscpu |grep "CPU MHz"|awk  '{print$3}'
sleep 4

echo -e "\nThe Kernel Version of the server is\n"
uname -r|awk -F- '{print$1}'
sleep 4

echo -e "\n The System has $(arch | awk -F_ '{print$2}') bits"
sleep 4


echo -e "\n The System Hostname is $HOSTNAME"
sleep 4

echo -e "\n The IP address is \n"
ifconfig enp0s3|grep inet|head  -1|awk  '{print$2}'
sleep 4
                                                                                       1,1           Top

echo -e "\n The DNS address is \n"
cat /etc/resolv.conf|grep nameserver |head -1|awk  '{print$2}'
sleep 4


clear

echo -e "\nAll opened ports listed below\n"
ss -tulpn |grep LISTEN
sleep 6

echo -e "\nThe Manufacturer is \n"
dmidecode -t system|grep  Manufacturer |awk '{print$2,$3}'
sleep 5


echo -e "\nTo tell  the System is Virtual or Physical? \n"
dmidecode -t system |grep  Family|awk  '{print$2,$3}'
sleep 5


echo -e "\n The Mac address is\n"
ifconfig enp0s3|grep  ether|awk  '{print$2}'
sleep 5

exit 0
                                                                                      61,1          60%
