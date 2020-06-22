---
layout: post
title: Calendly Scraper
subtitle: Scraping Calendly for available dates
image: https://media.glassdoor.com/sqll/1268317/calendly-squarelogo-1591106593677.png
tags: [Web Scraping, Python, Calendly, Calendar]
---

Problem: My interview was canceled and I was left with a very late time slot.  
Solution: Write a script that can be scheduled to run and check for any new availability.  

This was my first foray into web scraping for a personal project instead of an assignment. The first part of web scraping is investigation: 
what does the website of interest look like?

![calendar](/img/lambda_calendly.jpg)

Next, the investigation continues by opening up the source code in your browser; I used Chrome which has developer tools. 
Then, I clicked around on the site and watched for changes of interest to show up in the console. Inspect elements,
perform some requests, get a vague idea how the site is setup. Eventually I found in the network section (specifically the XHR)
the actual API calls of interest:

![API Call](/img/lambda_calendly_XHR.jpg)

These were the true URLs of the API calls that would ping the servers for date availabilities. Scanning through the URL I could 
easily setup different dates to search. After slicing appropriately through the JSON returned, I could iterate to return just available days.
  
Since this script will be running in the background I wanted a acoustic indication that a date was found.  On Windows this can be done with pywin32:
```
import win32com.client as wincl
speak = wincl.Dispatch("SAPI.SpVoice")
speak.Speak(f"{date} has available slots")
```

Now I had an audio indication whenever the script picked up an available date within my search. 
Finally, there was the task of looping through the script. One option is to use the `time` module and slap `time.sleep(1000)` 
at the bottom of a while loop. The while loop would be `while True:` which is a rather unsavory way of handling things in my opinion.
The alternative method was to use a batch file (`.bat`). This was relatively simple:  

```
:loop
"path/to/python.exe" "path/to/script.py"
timeout /t secondsyouwantbetweenloops /nobreak
goto :loop
```
And that's it, just running the `.bat` file will open the console and loop through the script as desired!

[Github Repo](https://github.com/JonNData/calendly-scraper)
