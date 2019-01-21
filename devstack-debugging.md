## Devstack Debugging

* Fix cinder volume group error after restart
  ```
  sudo losetup -f --show /opt/stack/data/stack-volumes-lvmdriver-1-backing-file
  sudo systemctl restart devstack@c-vol
  ````
