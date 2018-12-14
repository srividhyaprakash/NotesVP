# Steps:

## Installation and Basic Setup

* Log in to any ttsv-shell
* Copy this folder to your ttsv-shell or Unzip the zip file.
* Command to unzip the zip file: "unzip <filename>""
* Example: "unzip mx_to_usf_tool.zip"
* Navigate to the folder using appropriate "cd" commands.
* Install the necessary libraries using the command "pip install -r requirements.txt"
* Run "python3 FrontEnd.py"


#### Code

```
unzip mx_to_usf_tool.zip
```

```
cd mx_to_usf_tool
```

```
pip install -r requirements.txt
```

```
python3 FrontEnd.py
```






## Important Prerequisites:

*  Input XML configuration should be in the MX formatted XML mode. (XML is very important. Not the config file).

	* To generate the configuration file from your current MX router, 
		
		* run the following command from the CLI mode -  


        ```show configuration | display xml | save <filename>.xml```

*  The router should be in the USF mode.

	* To check for the current mode in the router, 

		* run the following command in CLI mode -

         ```show system unified-services status```

*  The router should contain the same hardware as the configuration file being given as the input.
 i.e fpc's should be sufficiently present in the router. Else a hardware error might occur.


## Output File Format and requirements

1. USF XML file (named after the Input XML file)
2. USF cfg file named as per given input or as per input file name
3. unclean USF cfg file (Kindly ignore this)

### USF FILE (XML FORMAT)
> For the XML format USF file, it is enough to select the XML option in the tool.

### USF FILE (CFG FORMAT)
> For the Cfg format in the USF mode, please specify the router name, hostname and password to the router.



# Other Optional Inputs:

* -v = Verbose (Display debugging Information)



# Frequently Asked Questions (FAQ)


1. Where do the output files get stored?
	
	* They get stored in the same location as the directory you ran the ```FrontEnd.py``` file

2. What features does the tool support? 

	* NAT, stateful-firewall, IDS are currently supported. Additionally all *interfaces*, *routing-options*, *forward-options*, *routing-instances*, *policy-options*, *firewall*, *applications*, *class-of-service*, *bridge-domains*, *event-options* hierarchies are currently supported.

3. Can I convert from USF mode to MX mode?
	
	* No, at the moment, the tool has the capability to convert the MX XML file to USF mode.

4. Will I definitely need the same amount of hardware in the router as present in the input XML file?

	* Yes, when converting to the JSON format *cfg* file, the tools logs in to the router specified where a *commit check* is performed. In order for this to pass, the router needs to have the same or more hardware.

5. I have 5 cards in my router. I am only configuring for 3 slots in my XML file. Will this be a problem?
	
	* No, as long as there are 3 or more cards in the router used, this will not be a problem.

6. I have 3 cards in my router. The XML input file currently has a configuration for 7 cards. Will this be a problem?

	* Yes.

7. I have my card in the 4th slot in my router. I have my input XML configuration with interfaces configured for the 2nd slot. Will this be an issue?

	* No, as long as the number of slots are sufficient, this would not be a problem. Please note, the configuration, if commited to this same router, will not work.

8. Can I change the size of the boxes present in the front end of the tool?

	* Yes, you can, but you will have the modify the source code for it.

