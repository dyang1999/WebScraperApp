# WebScraperApp

## Description

A webapp hosted on your local server to scrape various textual content from static websites.
To operate the webapp, enter the URL into the search bar, followed by the relevant tags nesting the content one wishes to scrape and press the scrape button to obtain the required content.
Download results as pdf, html files are available.

# Part I Getting Started

* Folder can be downloaded to any convenient working destination, ie. desktop.

### Setting Up Dependencies and Virtual Environment 


* To build a virtual environment:

Change directory to the folder, "WebScraperApp-main" in the terminal 

``` 
cd C:\Users\Daniel\Desktop\WebScraperApp-main
```
Enter the following line into cmd window/terminal to build virtual environment in the project folder

``` 
python -m venv env
```

(For windows) To enable the virtual environment, in the current directory enter:

``` 
env\Scripts\activate
```
(For mac) To enable the virtual environment, in the current directory enter:
``` 
env\bin\activate
```
* Once the virtual environment has been activated ie (env) will be shown before the terminal prompt,

* pip install the following python libraries  --  requests, flask_paginate, Flask, beautifulsoup4, lxml (version details found in requirements.txt)
                                             

## Executing the program

* To load up the webapp, enable the virtual environment in the project folder and enter the following into the cmd/terminal:

```
python app.py
```
* Access the local host url, http://127.0.0.1:5000/, in your internet browser.


# Part II Scraping instructions

https://www.securityweek.com/threat-actor-abuses-microsoft%E2%80%99s-whcp-sign-malicious-drivers will be used as an example to demonstrate the app's functionalities. 

1. Upon launching the webapp, if the input url is valid, a green alert will be shown along with the html of the website.

  ![Imgur](https://i.imgur.com/rcoZv3N.png)
  ![Imgur](https://i.imgur.com/sXRqzRB.png)

2. Inspect orginal website for the tags containing text that you wish to scrape. 
- In this case, I wish to scrape the title "Threat Actor Abuses Microsoft’s WHCP to Sign Malicious Drivers" which is located under the h2 tag, with a class, "page-title".       Input "h2" into the "tag name" row. Input "page-title" into the "CSS class" row (optional, it will be compulsory if the website has other instances of h2 tags cotaining       text)

  ![Imgur](https://i.imgur.com/dedDzGk.png)
  
- I wish to scrape the body of the article as well. Upon inspection , there are 2 components where test is found, the sypnosis in bold and the main body paragraphs. All of     which are encapsulated by different immediate tags, <span> and <p>s respectively. As such going up a level in the html markup language we see <div class="content clear-       block"> encapsualting both areas of interest. Therefore we key in "div" into the "tag name" row and "content clear-block" into the "css class" row.
  
  ![Imgur](https://i.imgur.com/HNvOWMo.png)
  
3. Press "add" to include new markers and press "scrape" when you have included everything you need.
  
  ![Imgur](https://i.imgur.com/upCdjDw.png)
  
4. Result page example
  
  ![Imgur](https://i.imgur.com/9UTZLZY.png)
  
5. "Print" page as a PDF or "Download" content as a HTML file
  
  HTML:
  ![Imgur](https://i.imgur.com/3EdQpEK.png)
  
  PDF:
  ![Imgur](https://i.imgur.com/k05ean4.png)



## Authors

Daniel Yang

## Version History

* 0.1
    * Initial Release

## Future works
* dynamic scraping functionalities
