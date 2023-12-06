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
Eventually, with the help of a group member I learned that I needed to first copy my ssh files into my WSL into a folder I created called ".ssh", I then used the chmod command to give the public ssh key (z_os.pub) so that I could read and write it, to give these permisions, I used the chmod command with the -600 flag. 

Finally I was able to ssh in using my user id, and the ibm ip, along with the -i flag which allowed me to give the directory of where I had stored my private key.

## Tuesday 09-26-2023

Today I got a lot of work done, I started off by ssh'ing into Z_OS and then running bash like I figured out how to do last time

I then started following igor's email that he sent and installed the new Z_OS meta and after some trial and error I managed to use the same info from my ssh efforts to use the sftp command and to sftp into Z_OS

I then used the "put" command to move the meta file that I had installed into the Z_OS system and directly quit, before ssh-ing back into the Z_OS system

Unfortunately I was supposed to put my files within a folder I had created called "dev" but I hadn't done that, so i quickly made the needed directory with the "mkdir" command, along with a .ssh directory for later, and used the "mv" command to move the correct files

I then used the "pax" command to get the pax, and used "init zopen" to initialize Z_OS

Once Z_OS had finished initializing I installed git and also installed vim while I was at it

Finally I got started on the steps of porting git, as that had been our decided way of getting used to porting to Z_OS

First I started by creating a new ssh public and private key on the Z_OS system, and stored the public key on on my github account by using the cat command to open it up so I could copy and paste it

Finally I used a few commands to clone gitport from github, and set it up on path

The last step was to build gitport but it takes a long time and class was almost over so I stopped there

## Friday 09-29-2023

Today I sshed in normally and cded into my gitport folder  before attempting to build gitport

Unfortunately I wasnt able to run the command
				
I tried to figure out whats wrong with path cuz thats why zopen isnt working
				
Eventually I learned that I have to build config every time
				
finally I ran 
```shell
zopen build -vv
```
and started building gitport after using cd to ented the gitport folder

But then I got an error because it didnt have my github account
				
So I used these commands to tell it my account
```Shell
git config --global user.email "email"
git config --global user.name "name"
```

And that was it for the day because it would take too long to try and build it

## Tuesday 10-03-2023

Today I attempted to build but ran into an error that seemed to be caused by perl

So I upgraded perl, but had to close it halfway through

So I reopened the terminal but had to uninstall perl as it now had an error

I then reinstalled perl which took the rest of the class

## Friday 10-06-2023

Today I again tried to build gitport

However, I ran into a error that prevented me from building

I used this command on the log file
```Shell
cat <.log> | grep error
```

to attempt to focus in on what was causing the error, but it didn't help, so rather than using the usual build command

```shell
zopen build -vv
```

I used a new one suggested by Igor

```shell
zopen build -u -vv
```

This command upgraded my libraries, but I still ended up getting an error