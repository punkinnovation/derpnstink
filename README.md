# derpnstink

The goal is to find 4 flags and get some root.


## nmap

![Alt text](./nmap.png?raw=true)


## Browse to site, flag 1

Flag 1 is found looking at the source code and scrolling all the way to the bottom of the page. Also a src to a text file that mentions the hosts file. I'm not sure if it made a difference, I changed it after finding the note. It does mention a username for 'stinky'.

![Alt text](./hosts.png?raw=true)

![Alt text](./flag1.png?raw=true)


## dirbuster

weblog dir identifies a Wordpress installation.

![Alt text](./dirbuster.png?raw=true)


## wordpress

admin/admin works to login but not much available.

![Alt text](./admin.png?raw=true)


## wpscan

wpscan identifies a vulnerable plugin which is listed in Metasploit for shell and a couple of users.

![Alt text](./wp_plugin.png?raw=true)

![Alt text](./wp_users.png?raw=true)


## low shell

Run the exploit

![Alt text](./lowshell.png?raw=true)



## mysql

The wp_config.php contains the DB creds. Pull the hashes from wp_users and crack hashes. unclestinky:wedgie57

![Alt text](./hashcat.png?raw=true)


## flag2

Logging in to wordpress as unclestinky shows flag 2 post

![Alt text](./flag2.png?raw=true)


## find key

SSH requires a key, but FTP as stinky with wedgie57 allows to drilldown to files/ssh/ssh/ssh,etc to get the key for stinky SSH

![Alt text](./ftp.png?raw=true)



## flag3, user shell

SSH to the vm as stinky with the compromised key, find flag 3 in dir listings.

![Alt text](./stinkyshell.png?raw=true)


![Alt text](./flag3.png?raw=true)


## pcap

File mentions pcap, found password in the pcap for POST methods. 

![Alt text](./pcap.png?raw=true)

![Alt text](./mrderp.png?raw=true)


## sudo

mrderp user needs a key for SSH but su as stinky works fine, sudo shows ALL users for files

![Alt text](./sudo.png?raw=true)


## root

<pre>
\(*_*)
  ( (>
  /  \
  </pre>

![Alt text](./suid.png?raw=true)

Create executablefile, run as root for root

![Alt text](./root.png?raw=true)


## flag4

cat root flag for victory

![Alt text](./flag4.png?raw=true)


## thanks

Thanks out to securekomodo for the sweet VM.
