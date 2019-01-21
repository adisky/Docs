## Devstack Debugging

* Fix cinder volume group error after restart
  ```
  sudo losetup -f --show /opt/stack/data/stack-volumes-lvmdriver-1-backing-file
  sudo systemctl restart devstack@c-vol
  ````
  
  * Fix ssh to vm after reboot
  ```
  route -n
  sudo ip route add default via 192.168.200.1
  sudo ifconfig br-ex 172.24.4.1 netmask 255.255.255.0 up
  ```
