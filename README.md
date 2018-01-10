[![Build Status](https://travis-ci.org/fatalglitch/nestivus.svg?branch=master)](https://travis-ci.org/fatalglitch/nestivus)
# Nestivus

### Nessus for the rest tiv us

Simple utility to automate scanning, reporting, and delivery of reports from Nessus vulnerability scanners.
Written to fulfill a need to better automate scans and reporting across multiple networks, this tool
provides easier methods to execute automated scans using a scheduling tool of choice. 

Work Conducted by:
---------------------------------------
* Tom Callahan [Twitter]@tomtheitguy

Current Platforms Supported:
* Ubuntu 16+
 
## Get Started
```
git clone https://github.com/fatalglitch/nestivus
cd nestivus
pip install -r requirements.txt
```
The example.cfg file contains settings specific to your environment,
you will need to review and update to match your network.

Once your config file is updated, you can run the scanner

```
./nestivus -c <config_file>
```

## Config File Format
The config file contains several sections which need to be setup for your specific environment.
### Server Section
Input your Nessus login and password, along with the scanner hostname or IP Address, and port
### Scan Section
Input the name you want for the Scan which is created, along with the description for this scan.
The "enabled" parameter defines if the scan is set to enabled when created. You should leave this as True
The launch parameter defines the launch style for the scan. You should leave this as "ON_DEMAND"
Targets is used to dictate which targets you will be scanning. This is a comma seperated list and can include single IP addresses or CIDR notation networks
### Schedule
The scheduler option can be enabled by invoking the -s flag when running the script. These settings dictate when the scan should execute
Minute, Hour, and Day should be either 2 digit values, or * to indicate wildcard.
LastOfMonth is used to indicate the scan should be run on the last Monday, Tuesday, etc. of the month. Valid values are days of the week, and the values are no case sensitive
### Report
Reports are generated based on the values in this section
"format" can be one of html or csv. Nessus currently does not support PDF generation
"types" indicates the type of report to generate. The example config contains all available types. You can remove these to fine tune which report style you want.
"filename" is the prefix for the filename to be generated and emailed. The extension of the file should not be included.
### Email
Email is sent utilizing these config values. Of note specifically is the server and port of your mail server.
### Logging
Specify the log file and path. Debug can be enabled by passing -d to the script at runtime.

## Testing Options
Testing can be performed by using nohup execution like below:
```
nohup ./nestivus -c example.cfg &
```
This will allow execution of the script in the background, and you can then use tail to watch the script execute. Debugging can be enabled by adding the -d flag to the nohup execution
```
nohup ./nestivus -c example.cfg -d &
tail -f /tmp/logfile.log
```
The logfile location and name is based on what you have set in your configuration file.
## Scanning Policy
The scanning policy is based off of Example_Policy.json, which is loaded by default.
You can modify this to customize your scan policy, and use the '-p' flag to choose the policy for the scan.

## Options
```
usage: nestivus [-h] [-c CONFIG] [-t TARGETS] [-p POLICY] [-d] [-e]

optional arguments:
  -h, --help            show this help message and exit
  -c CONFIG, --config CONFIG
                        config file to use
  -t TARGETS, --targets TARGETS
                        targets for the scan
  -p POLICY, --policy POLICY
                        Scanning Policy File to Use
  -d, --debug           enable Debug Logging
```
