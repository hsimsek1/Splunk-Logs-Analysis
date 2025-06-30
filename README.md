# Splunk Logs and Investigations

In this project I will be using a large dataset of over 100,000 events containg 15 domains, [Splunk Enterprise](https://www.splunk.com/en_us/products/splunk-enterprise.html). 

The main objective of this project is to analyze and visualize: 

1. DNS Logs
2. FTP Logs
3. HTTP Logs
4. Tunnel Logs
5. STMP Logs
6. DHCP Logs

and also use many of the available Search Processing Language (SPL) tools to craft efficient and complex searches: [Splunk and SPL](#splunk-and-spl)

[WHAT HAVE YOU LEARNED HUSEYIN?]

## Table of Contents

[CREATE A TABLE OF CONTENTS]

## Splunk and SPL

In this section I will focus on the SIEM capabilities of Splunk and go through its many data analysis tools. I will also use Splunk Processing Language (SPL) to conduct various searches, filters, transformations, and visualizations. 

### Analyzing DNS Logs

To begin creating basic SPL commands, I will use a Splunk Index named **main** and a sourcetype called **csv** . 

For starters I first search `index=main sourcetype=csv`:

Reference-style: 
![alt text][logo]

[logo]: https://github.com/hsimsek1/Splunk-Logs-Analysis/blob/main/dns-log-analysis/screenshots/38b5e7c0537535bb17aa6b2d657868e7.png
