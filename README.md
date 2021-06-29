# WebScraperApp

## Description

A webapp hosted on your local server to scrape various textual content from static websites.
To operate the webapp, enter the URL into the search bar, followed by the relevant tags nesting the content one wishes to scrape and press the scrape button to obtain the required content.
Download results as pdf, html files are available.

## Getting Started

* Folder can be downloaded to any convenient working destination, ie. desktop.

### Setting Up Dependencies and Virtual Environemnt 


* To build a virtual environment:

Change director to the folder WebScraperApp-main in the terminal 

``` 
cd C:\Users\Daniel\Desktop\WebScraperApp-main
```
Enter the following line into cmd window/terminal to build virtual environement in the project folder

``` 
python -m venv env
```

(For windows) To enable the virtual environment, in the same destination enter:

``` 
env\Scripts\activate
```
(For mac) To enable the virtual environment, in the same destination enter:
``` 
env\bin\activate
```
* Once the virtual environment has been activated ie (env) will be shown before the terminal prompt,

* pip install the following python libraries  --  requests, flask_paginate, Flask, beautifulsoup4, lxml (version details found in requirements.txt)
                                             

## Executing the program

* To load up the webapp, enable the virtual environement in the project folder and enter the following into the cmd/terminal:

```
python app.py
```
* Access the local host url, http://127.0.0.1:5000/, in your internet browser.


# Scraping instructions

https://www.securityweek.com/threat-actor-abuses-microsoft%E2%80%99s-whcp-sign-malicious-drivers will be used as an example to demonstrate the app functionalities. 

Upon launching the website, 





## Authors

Daniel Yang

## Version History

* 0.1
    * Initial Release

## Future works
* dynamic scraping functionalities
