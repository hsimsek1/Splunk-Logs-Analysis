# Splunk Logs and Investigations

In this project I will be using a large dataset of over 100,000 events containg 6 different fields, [Splunk Enterprise](https://www.splunk.com/en_us/products/splunk-enterprise.html). 

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
![](https://github.com/hsimsek1/Splunk-Logs-Analysis/blob/main/dns-log-analysis/screenshots/38b5e7c0537535bb17aa6b2d657868e7.png)

This query is displaying raw events from the main index where the sourcetype is csv. This means that Splunk is ingesting data that is from a file uploaded called dns_logs_100k.csv. It is basically showing all the events in the file. The "Event" column shows parsed fields time, src_ip, dest_ip, domain, query_type and response_code. You can see entries such as (2025-06-28T10:00:08,	192.168.1.138,	8.8.8.8,	random23.co,	A,	NOERROR). 

By doing this I'm also ensuring that the data from dns_logs_100k.csv is parsed correctly and that I'm not seeing any unexpected results.

Next using a splunk quiery I try to find events where their "response_code=NXDOMAIN", reponse_code can either equal NOERROR (No error) or NXDOMAIN (which means non-existent domain). By doing so I am 	trying to find possible typos, malware, phishing, or misconfiguration.

![](https://github.com/hsimsek1/Splunk-Logs-Analysis/blob/main/dns-log-analysis/screenshots/eee4c25e3772350d34b9689e48545434.png)

The data returns 15 different domains which are (news-update.today, random23.co, securelogin.info, loginerror.com, test.org, microsoft.com, ads-server.net, phishy.biz, malware.update.ru, suspicousdomain.xyz, openai.com, google.com, safesite.io, example.com, data-leak.net). 

Instantly I can point out some malicious looking websites such as malware.update.ru, phishy.bz, and etc.

![](https://github.com/hsimsek1/Splunk-Logs-Analysis/blob/main/dns-log-analysis/screenshots/5572455f0c73077a3dbdbc489529978a.png)
