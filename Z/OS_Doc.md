## Important Commands

ssh in - 
```shell
ssh <user>@128.168.129.26 -i ~/.ssh/z_os
```

set up zopen config - 
```Shell
. /dut2/zopen/etc/zopen-config
```
## Friday 09-22-2023

Today I worked on signing in to the Z_OS operating system. This started off with some issues. For one, despite having created an SSH key and sent it to Igor I was unable to sign in.
![](pic1.png)
Eventually, with the help of a group member I learned that I needed to first copy my ssh files into my WSL into a folder I created called ".ssh", I then used the chmod command to give the public ssh key (z_os.pub) so that I could read and write it, to give these permisions, I used the chmod command with the -600 flag. 

Finally I was able to ssh in using my user id, and the ibm ip, along with the -i flag which allowed me to give the directory of where I had stored my private key.
![](pic2.png)
