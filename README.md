# msfvenom_creator


msfvenom_creator automatically creates a payload and listens with multi/handler. 


## Installation

```sh
$ chmod +x msfvenom_creator
```

## Usage
Specify LHOST and LPORT as arguments.


```sh
$ ./msfvenom_creator -h
Usage:
    msfvenom_creator [LHOST] [LPORT]

Options:
    --version, -v     print msfvenom_creator version
    --help, -h        print this
    --ip              print ip v4 address
```

### No argument

You can now select the address and port without any arguments. <3

```sh
[+] Your IP address
1 : 127.0.0.1
2 : 192.168.xxx.xxx
3 : 10.10.xx.xx

[-] Select ip address : 3
[+] Your selected ip address : 10.10.xx.xx

[-] Input listen port : 4444
Your LHOST is 10.10.xx.xx LPORT is 4444

Please select a payload.
```


## IP option
Show your ip v4 address.


```sh
$ ./msfvenom_creator --ip

[+] Your IP address
127.0.0.1
192.168.xxx.xxx
10.10.14.xx
```

## Create payload
Select payload number.  
When you create a stager payload, it automatically listens with multi / handler.  


```sh
Please select a payload.
[-] Binaries Payloads

[*] 1 : Linux Meterpreter Reverse Shel
[*] 2 : Linux Meterpreter Reverse Shell x64
[*] 3 : Linux Bind Meterpreter Shell
[*] 4 : Linux Bind Shell
[*] 5 : Windows Meterpreter Reverse TCP Shell
[*] 6 : Windows Meterpreter Reverse TCP Shell x64
[*] 7 : Windows Reverse TCP PowerShell x64
[*] 8 : Windows Reverse TCP Shell
[*] 9 : Windows Reverse TCP Shell x64
[*] 10 : Mac Reverse Shell
[*] 11 : Mac Bind Shell

[-] Web Payloads

[*] 12 : PHP Meterpreter Reverse TCP
[*] 13 : ASP Meterpreter Reverse TCP
[*] 14 : War

[-] Scripting Payloads

[*] 15 : Python Reverse Shell
[*] 16 : Bash Unix Reverse Shell
[*] 17 : Perl Unix Reverse shell
```

## Demo
![](https://user-images.githubusercontent.com/16620233/65217440-035d5d00-daef-11e9-9618-2be2141df7fc.gif)

## Command
```sh
# cp msfvenom_creator directory in path
# ex.
$ echo $PATH
/root/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
$ cp msfvenom_creator /root/bin
$ chmod +x /root/bin/msfvenom_creator

$ msfvenom_creator
```

## Reference

- https://www.metasploit.com/  
- https://www.offensive-security.com/metasploit-unleashed/msfvenom/
