## Attach EBS volume to EC2

- first check if we can see the volume after running the `df -h` command
  ```
  $ df -h
  ```
- now list all the blocked device in linux system `lsblk`
    ```
    $ lsblk
    ```
- now check if there is any filesystem for the volume
    ```
    $ sudo file -s /dev/xvdf
    /dev/xvdf: data {this will be the output if there is none}
    ```
- if no filesystem then create a new one
   ```
   $ sudo mkfs -t xfs /dev/xvdf
   {here xfs is the file system name}
   ```
- check again to confirm `$ sudo file -s /dev/xvdf`
- create a mount dir `$ sudo mkdir -p /var/pv/data`
- create the mount `sudo mount /dev/xvdf /var/pv/data`
- now run `$ df -h` to confirm that the filesystem has mounted successfully
- run `lsblk` you will see the mount path