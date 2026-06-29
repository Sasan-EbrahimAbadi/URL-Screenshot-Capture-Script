# URL-Screenshot-Capture-Script


A simple Bash script that captures screenshots of a list of web pages using Cutycapt. Each screenshot is saved with a timestamp and sequential number, making it easy to identify when it was captured.

## Overview

This script:

Reads a list of URLs from a text file.

Visits each URL using Cutycapt.

Takes a screenshot of the webpage.

Saves each screenshot with a unique filename containing:

Current date and time

Sequential image number
______________________________________

## How It Works

Step 1: Initialize Counter

x=0

Creates a counter used to uniquely number each screenshot.

Step 2: Read URLs

for i in $(cat /home/Local_address/Url_List)

Reads each URL from the Url_List

Each line in the Url_List text file should contain a single URL.

Step 3: Increment Counter

x=$((x+1))

Increases the screenshot number.

Example:

1
2
3
...

Step 4: Capture Screenshot

cutycapt \
    --url="$i" \
    --out=/home/Local_address/Filename_$(date +%m%d%H%M)_$x.bmp

Cutycapt opens the webpage and saves a screenshot.

The filename is composed of:

Filename_
MMDDHHMM
Counter
.bmp

Example:

Filename_06271530_1.bmp

Filename_06271530_2.bmp

Filename_06271530_3.bmp

where:

06 → Month

27 → Day

15 → Hour

30 → Minute


## Usage

1. Install Cutycapt

On Ubuntu/Debian:

sudo apt install cutycapt

Verify the installation:

cutycapt --help

_________________________
## Note: There are many applications that can capture screenshots of web pages. Most of them follow this workflow:

Open a browser and navigate to the specified URL.

Wait for the web page to load.

Capture a screenshot.

Close the browser.

This approach works well for occasional screenshots, but it becomes less reliable when capturing screenshots over an extended period (weeks or months). As the target website grows or implements anti-bot measures, page loading may become significantly slower or even stall. In such cases, screenshots may be captured before the page has fully loaded, resulting in incomplete or blank images.

To address this issue, you can use CutyCapt. Unlike tools that rely on automating a full browser session, CutyCapt renders the web page in a lightweight, headless environment and captures the screenshot directly. This makes it more suitable for long-term automated screenshot generation.
