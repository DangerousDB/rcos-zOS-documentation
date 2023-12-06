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

## Sunday 10-08-2023

Today I tried using a new build command

```shell
zopen build -f
```

which is supposed to force a build. unfortunately I again ran into the same error

## Friday 10-13-2023

Today I updated my libraries and again attempted to force a build, but ended up having the same error as usual

## Tuesday 10-17-2023

Today I took a new approach suggested by Igor, I used a command to check how far behind my build of gitport was
```shell
git diff
```

when I saw that my build was behind, I removed it
```shell
rm -rf git-2*
```

I then copied the latest build of gitport and then had to leave it for the day as I was out of time

## Monday 10-23-2023

Today I attempted to build my new build of gitport but ended up running into an error again

This was a new error though, specifically an error with curl

## Tuesday 10-24-2023

Today I gave up on gitport and started solving an easy beginner issue having to do with command accuracy on the meta page, I made a branch of the meta, added the change, and then submitted a pull request for my branch, explaining what my changes did, and linked the issue my pull request would solve

## Thursday 10-26-2023

Today I saw that my pull request had one approval and one denial, requesting for me to make some changes. I added the requested changes, committed the new version, and sent a message explaining that I had updated my branch

## Tuesday 10-31-2023

My pull request got approved

## Tuesday 11-07-2023

Today I decided to start working on helping to port libmd. To start I copied over the latest build from github and attempted to build it. However I ran into an erro

This is an interesting error, because it seems to come from zopen building, not the actual code, my current guess, is that the port passes some information during the build process that is the wrong format for zopen build which causess it to blow up, however I decided to upgrade my libraries, as it could also be a problem on my end rather than with the code

Unfortunately I wasnt able to complete my upgrades so I will continue that some other time

## Tuesday 11-14-2023

Today I ran into an error when trying to continue completing my upgrades. What happened was that since I had to stop upgrading in the middle last time, the computer got confused thinking the process was still ongoing even though it wasnt. 

The terminal told me that process '423' was holding me back, so I used a command to see what processes were ongoing

```shell
ps -e
```

after confirming that process 423 was ongoing, I used another command to kill it so I could continue upgrading

```shell
kill -SIGKILL 423
```
