# CrazyParser
CrazyParser is a python utility to automate the generation of potential typosquatted domain names using URLCrazy. CrazyParser takes an input file of domain names, a list of domains previously identified by URLCrazy, and generates an email notification indicating whether new typosquatted domains have been identified.  

This was originally created to notify security analysts of potential new typosquatted domains that may be used in a phishing attack.  Security analysts can use this information to enhance monitoring or place blocking in web proxies to prevent access to the phishing domain.

# CrazyParser files
 - crazyParser.py - Python utility for automating URLCrazy queries
 - mydomains.csv - contains all domains you wish to query for typosquatting
 - knowndomains.csv - contains domains previously identified valid or typosquatted domains

# mydomains.csv format
mydomains.csv contains a list of one or more domains, one per line.

# knowndomains.csv
knowndomains.csv contains domains previously identified as either typosquatters or valid domains. The format of this file is one entry per line in the form of: domain.tld,reason.  Known domains must have a header row containing the text "Domain,Reason".  The reason is not used by crazyParser.  This field should be populated with your description of the domain.

To populate knowndomains.csv, use URLCrazy to generate output for review.  For each existing domain, review the entry to determine if it is a valid domain or a typosquatter.  Record the domain name and whether the domain is valid or a typosquatter in this file.

# Usage
python crazyParser.py.

crazyParser takes each domain listed in mydomains.csv and uses URLCrazy to generate a list of typosquatted domains.  Each registered domain is compared against knowndomains.csv.  If there are no new domains discovered, crazyParser will generate an email containing an all clear message.  If any new domains are discovered, the output will be placed in a csv file and attached to an email stating a review is necessary.  This output should be reviewed and the knowndomains.csv file should be updated with the new entry.
