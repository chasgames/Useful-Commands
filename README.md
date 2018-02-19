*Commands that I would not otherwise use/remember* 

* will eventually format this with fancy hyperlinks and the like*

test

**General commands**


	sudo !! (run last command as root (!! means to run the last command))

	pkill -9 -f “program” (kill all instances of a program)
	
	Source .bashrc (enable the updated bashrc)
	
	ls -laht (long,all,humanreadable,time)
	
	du -sh file_path (see size of directory)
	
	awk '{print $3;}' (this will print the 3rd word of the output, if you ran it against this sentace it will return the word print)

	using &! after running a command will put it fork the command to the background (&) and then disown (remove from the 'jobs' list) the command (!)




**Status commands**

	uname -a (show kernel version etc)

	less (pipe commands to this for easy reading (ls -la | less)

	df -h (drive information)

	free (memory information)

	ps -ef (list processes.)

	lsof (list open files)
	
	lsof -Pi:<portnum> (list services running on port) (run as root or sudo)

	ps aux (current processes, aux flags = a - processs for all users, u - display process owner, x - 	show processes not attached to terminal)
	
	smartctl -a /dev/sda (lists abundence of information relating to hardrive health
	
	dmesg -H (dmesg with time stamps and in $PAGER (less default))	

**systemd**
	systemctl list-unit-files | grep enabled (startup programs)


**user commands**
	
	usermod -aG wheel *username* (add user to the wheel group)
	chage -d 0 <username> (make sure the user changes their password on login)
	
**file system**

fuesr -cv <mountpoint> (check what processes a mount is using, useful when umounting)

**grep**

*you could just read the man page*
	
	grep -i (case sensitive)
	grep -v (!=)

**kill**
	
	kill pid (kill a process)
	kill -STOP pid (stop (freeze) a process)
	kill -CONT pid (resume a stopped process)
	kill -INT  pid(ctrl c)
	Kill -KILL pid (also use kill -9. This absoulty destroys a process. Forcefully removes it from ram and ends its life without giving it any chance at shutting itself down gracefully)

**find**

	 find . -name "thing you want to delete" -delete (use find to delete things that you have found)
	 find . -name '*.pyc' -delete (an example, deleting anything that ends in .pyc)


**DD**

*data duplicatior(destroyer)*

the if and of stand for input file and output file

	dd if=/dev/sda of=/dev/sdb (clone one hdd to another hdd)
	dd if=/dev/sda4 of=~/hdadisk.img (backup of sda4 partition and name it hdadisk.img)
	dd if=hdadisk.img of=/dev/sdb3 (restore from .img file to dev/sdb3)
	dd if=/dev/zero of=/dev/sdb (wipe /dev/sdb. /dev/zero is a special file that provides null characters)
	

**Rsync**


	rsync -a ~/dir1 username@remote_host:destination_directory ( synch to a remote host (push))

	rsync -a username@remote_host:/home/username/dir1 place_to_sync_on_local_machine ( sync 
	from remote to local (pull))

**Screen commands**


	"ctrl a"  is the modifyer so screen knows a command is coming

	screen (start screen)

	screen -r  (reattach screen)

	ctrl ac  (move between screens)

	ctrl ak (kill current screen)

	ctrl aw (list screens)

	ctrl an (new screens)

	ctrl ad (detatch back to shell)

	ctrl a[ (enters copy mode (enter once to copy and enter again to save it to clipboard))

	ctrl a] (paste what is copied)

	ctrl a,  a  (send commands to nested screen) 

	ctrl a, | - split the session (ctrl a tab to switch between them)

	ctrl a, S – splits the session differnetly

	screen -X -S SCREENID kill (kill attached screen session)

	screen -D -r  (reconnect to attached screen session)


**Vim**


	sudo -e file (edit file with root permissions but keep user vimrc)
	
	:w !sudo tee %  (save readonly file not opended as root)
	
	pandoc -f docx -t rst /patht/to/file.docx | vim - (edit word docs in vim, can change docx to odt for libreoffice)
	
	
**iptables**
	
*ip6tables for ipv6*
	
	iptables -t filter -A INPUT -s x.x.x.x -j REJECT (block the specified ip.) 
	
	-t table to use -A append -s source ip -j block method(REJECT, DROP).
	

**Git**
*soon (tm)*

**XTerm**

	shift insert (copy/paste)


**fail2ban**

	fail2ban-client status set <jailname (sshdisdefault)> unbanip x.x.x.x (unbans target ip)
	
**Tar**
	
	Tar -xzf ((e)xtract ze file!)
	Tar -czf (compress ze file!)
	
	
**ssh**
	
	$ ssh -L 9000:imgur.com:80 user@example.com (ssh tunneling (localhost:portnum(9000) to vist site))
	To exit out of a frozen ssh session press: 'enter' ~ . 
	
**ss**

*replaces netstat*

	ss (shows all tcp,udp and unix socket information)
	ss -l (show current listing sockets)
	ss -t -u -x (these flags are for showing tcp,udp and unix connections)
	ss -a (need to add to show listing sockets as well. Default is only established connections)
	ss dst x.x.x.x (show how you are connecting to an ip)
	
**tcpdump**
	
	tcpdump not port 443 (show packets that do not come from 443. This can be done with mutiple ports as well)
	tcpdump - "interface" (show packets from that a certain interface)
	tcpdump "protocol" (show only certain protocol. see /etc/protocols for a list
	
**docker**

	docker pull "image" (download docker images)
	docker images (list all images downloaded)
	docker start "image id" (stat image in background)
	docker attach "image id" (reattach docker image to the terminal)
    docker run "image" (run a docker image. This creates a new container which you then need to save by commiting it.)
	docker run -it "image" (run a docker image and access the shell)
	docker commit -m "message" -a "author" "container-id" "repo/name" (commit a new docker image)
	docker commit "containerid" "repo/name" (simplier docker commit)
	docker ps -l (list containerid)
	docker ps (list all running containers)
	docker ps -a (list all containers)
	docker stop "container-id" (stop a running container)
	docker rmi "image" (remove docker image)
	docker system prune --volumes
	
**docker-compose**
	docker-compose up -d
	docker-compose logs
	docker-compose down --rmi all

	

**ffmpeg**

	ffmpeg -f x11grab  -s 1366x768 -i :0.0 out.mkv (record screen, change size to be appropite to your display)

	
	
	
	
**Misc**

	python -m SimpleHTTPServer [port] (start a webserver serving the current directory)
	
	python -m http.server [port] (python3 of the above command)
	
	echo -n foobar | sha256sum (generate sha256 hash if "foobar" -n stops echo producing a trailing newline)
	
	badblocks -v /dev/sda (show badblocks on drive)
	
	pygmentize (cat with syntax highlighting)
	
	cd /usr/src/linux 
	make menuconifg 	(this command allows you to configure the kernel modules. You need to be in /usr/src/linux to do it)
	
	wget --mirror --convert-links --adjust-extension --page-requisites --no-parent (download webpage to read later)
	
	indent <file> -kr -i8 (idnet code to linux kernel coding style)
	
	ffmpeg -i input.mp4 -acodec libvorbis -vcodec libtheora -f ogv output.ogv (convert mp4 to ogg)
	
	
**Fun**

This should be a simulate a cointoss 100 times then tell you how many times it landed on heads

*for some reason it does not always work, but it eventaully will if you keep running the command*

	shuf -r -n 100 -e Head Tail > headtail | grep "Head" headtail | wc -l
	
most used commands and percentages of them
	
	history | awk '{CMD[$2]++;count++;}END { for (a in CMD)print CMD[a] " " CMD[a]/count*100 "% " a;}' | grep -v "./" | column -c3 -s " " -t | sort -nr | nl |  head -n10


# Distro Specific Commands

**Gentoo-specific-commands**
Reference commands that I might need in the future 
this used to be  its own repo but I did not think that was nessessary





*Bluetooth*
 
 Bluetooth seems to be turned on by default (at least the btusb radio device is.) This saps a lot of power and is the top consumer of power in powertop when the system is idle
 
 To turn it off:
 
      emerge -av net-wireless/rfkill
      
      rfkill block bluetooth 
      
      
      
      

*portage errors*

when running emerge -av package_name, sometimes it says required by package *www-clinet/w3m  imlib* for example

     this means that you need to create a file name after the package_name /etc/portage/make.use directory and paste in the "required by    package part of the error" This should work.
     
     
     
**CentOS**

*install extexted packages*

	yum install epel-release
	
*remove dump files*

centos creates dump files by default. These can ocassionaly take up a lot of space. TO remove them
	 
	 sudo find . -name "core.[0-9]*" -delete

configure networking 

	nmtui (easy mode)
	
Add a gpg key

	rpm -Uvh <key.rpm>
	rpm --import <key.txt>
	 
	 

	

**Debian**

*get number of packages installed*

	dpkg -l
	

**Fedora**

*allow access to extended free and non free repos

	sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

      
      

	
