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
