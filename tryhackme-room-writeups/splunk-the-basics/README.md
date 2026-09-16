# Splunk: The Basics — TryHackMe Writeup

> Room: https://tryhackme.com/room/splunk101
> Difficulty: Easy
> Focus: SIEM, Splunk, log analysis

![Platform](https://img.shields.io/badge/platform-TryHackMe-red)
![Focus](https://img.shields.io/badge/focus-SIEM%20%7C%20Splunk-blue)

## Overview

This room introduces the fundamentals of Splunk — ingesting data, searching, and using SPL (Search Processing Language) to filter and analyze logs.

## Tools & concepts

Splunk, SPL (Search Processing Language), indexes, basic search filtering

## What I worked through


Some of the things that I worked through in this room are the very basics of how Splunk works. I went through a tour of
the main menu. After this, I went through the process of uploading the TryHackMe example logs. Finally, I ran some example
commands to look at the possibilities of what Splunk can do. Beyond the guided steps, I looked at what putting in index=VPN_Logs looks like on its own. Doing this allowed me to see a clear timeline of logs, as well as multiple logs and their information.


![image of index=VPN_logs](tryhackme-room-writeups/images/screenshot_of_splunk.png)


## Key SPL / commands I picked up

index=: sets what index you would like to look for. This way, you do not have to look at everything at once. 
search: This allows for basic filtering. You can find things such as country, username, and Source IP.
stats count: allows you to count the number of events or results of a search.

## Key takeaway

Splunk can look very confusing at first, but understanding filtering helps narrow down events that could be suspicious activity. The next steps for me are to learn more about filtering and how to read these logs. 

## Why this matters for SOC/defensive work

Splunk is a part of a SOC analyst's everyday life. Understanding the tool and how to utilize it best will be imperative for the future of my career.

---

*This writeup does not include the room's flag values, in line with TryHackMe's writeup policy.*

*Written by Tyler Wood · [github.com/TDub3409](https://github.com/TDub3409) · [LinkedIn](https://www.linkedin.com/in/tyler-wood-301294328/)*
