# Raspberry-password-pi-recovery
Restore pi password - Raspbian password - raspberry password pi recovery

If you forgot the raspberry password with Raspbian, you can reset it! The procedure involves inserting the microsd on your PC and modifying the file inside the cmdline.txt (in boot partition of microSD) file by inserting at the end of the present string:

	"init=/bin/sh" (without the quotes)

Original string: 

	console=serial0,115200 console=tty1 root=PARTUUID=738a4d67-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait init=/bin/sh 
	
New String: 

	console=serial0,115200 console=tty1 root=PARTUUID=738a4d67-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait

save and unmount the sd from the pc and put it back in the raspberry

Start the rasp, wait for the prompt and type:

(all without quotes) 
  
	"mount -o remount, rw /"

type enter

	"passwd pi"

enter the new password followed by password confirmation.

type hours:

	"Sync"

Now you can turn off your raspberry, put the microsd back on the pc and delete the last part inserted from the cmdline.txt file: "init = / bin / sh" save, unmount the microsd from your pc and put it back in the raspberry. At startup, you should be able to log in with user "pi" and the new password you just set.

The procedure can also be performed with other users by replacing "passwd pi" with "passwd" following the user to whom you wish to change the password.
