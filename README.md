# NessScan
###https://www.github.com/fatalglitch/ness_scan

Simple utility to automate scanning, reporting, and delivery of reports from Nessus vulnerability scanners.
Written to fulfill a need to better automate scans and reporting across multiple networks, this tool
provides easier methods to execute automated scans using a scheduling tool of choice. 

Work Conducted by:
---------------------------------------
* Tom Callahan [Twitter] @tomtheitguy

Current Platforms Supported:
* Ubuntu 16+
 
## Get Started
```
git clone https://github.com/fatalglitch/ness_scan
cd ness_scan
pip install -r requirements.txt
```
The example.cfg file contains settings specific to your environment,
you will need to review and update to match your network.

Once your config file is updated, you can run the scanner

```
./ness_scan -c <config_file>
```

## Scanning Policy
The scanning policy is based off of Example_Policy.json, which is loaded by default.
You can modify this to customize your scan policy, and use the '-p' flag to choose the policy for the scan.

## Options
* -h to print the help menu
* -d will enable debug to log file
* -t specify scan target (this overrides the config file)
* -p specify policy template for scans