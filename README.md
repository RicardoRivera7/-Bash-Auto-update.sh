# Bash-Auto-update.sh
A small bash script that checks for any dependencies that need to be installed and then installs them if needed

```
<h5>
#!/bin/bash <br/>
# @Author: RicardoRivera <br/>
# @Date:   2021-05-23 18:15:36 <br/>
# @Last Modified by:   RicardoRivera <br/>
# @Last Modified time: 2021-05-23 20:00:06 <br/>
# <br/>
#	Auto-update <br/>
#	=========== <br/>
#	This is a short program that checks to  <br/>
#	see if any of your programs are out of date <br/>
#	and updates them if they are <br/>



# Internal Variables (user should not change), NC = no color <br/>
RED="$(tput setaf 1)" <br/>
GREEN="$(tput setaf 2)" <br/>
NC="$(tput sgr0)" <br/>
DEPENDENCIES=" " <br/>


#If anything needs to be updated i.e. dependencies then it does so <br/>
	function main() <br/>
	{	 <br/>

		Verify_Root 

		echo "$0:${GREEN} Setting Up... ${NC}"

		performingTask

		install_dependencies

		exit 0
	}


#lets user know that the script is currently running <br/>
	function performingTask() <br/>
	{ <br/>
		echo "${FUNCNAME}:${GREEN} Running Tasks... ${NC}" <br/>
	} <br/>

#In case an error occurs, it aborts the script <br/>
	function ErrorHandler() <br/>
	{ <br/>
		echo "${FUNCNAME}:${RED} Error Occured... Aborting Script ${NC}" <br/>
		exit -1 <br/>
	} <br/>

#installs dependencies if needed <br/>
	function install_dependencies() <br/>
	{ <br/>
		echo "$0:${GREEN} Installing Dependencies Please wait... ${NC}" <br/>

		ErrorHandler=ErrorHandler

		sudo apt-get update && apt-get -y install $DEPENDENCIES || ErrorHandler
	}

#checks to make sure you are running script as root <br/>
	function Verify_Root() <br/>
	{ <br/>
		if [ "$UID" != "0" ]; then <br/>
			echo "$0:${RED} you must be root to run this script :( ${NC}" <br/>
			exit -1 <br/>
		fi <br/>
	} <br/>

#Main function that runs script <br/>
	main $0 <br/>
</h5>
```
