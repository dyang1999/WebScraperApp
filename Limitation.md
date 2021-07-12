# Beautiful Soup / Requests limitations and challenges encountered

## Limitations of Requests library

While web scraping, often the error 404 was returned by beautiful soup triggered by requests extension. The likely cause was found to be the need to define a user agent to obtain website html. This can be done by declaring a false user agent. Official Documentation on https requests : https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent

Standard user agent list: https://www.whatismybrowser.com/guides/the-latest-user-agent/chrome

### Solution

``` 
>>> import requests
>>> url = "https://www.transfermarkt.com/jumplist/startseite/wettbewerb/GB1"
>>> headers = {'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36'}

# Make request with "User-Agent" Header
>>> response = requests.get(url, headers=headers)
>>> response.status_code
200   # success response

>>> response.text  # will return the website content
```
## Limitations of BS4 library

Certain websites are dynamically loaded - i.e html is loaded in by JavaScript. As a result errors as follows are often seen where there are either missing parents/ children tags or BS4 scrapping off JS.

![Imgur](https://i.imgur.com/UJ0iEqr.png)

### Solution

Loading in the HTML is therefore required, which can be resolved using Selenium (python library) which loads the webpage in a chrome driver. This solution works but often requires a side running brower to run the python based Selenium script.

### Alternative solution

Using JavaScript's Puppeteer extension to acheive simialar functionalities as Selenium without having to run a side browser or utilize a driver.

JS Code snippet applied to an Amazon website selling a book : 

```
const puppeteer = require('puppeteer');

async function scrapeProduct(url){
    const browser = await puppeteer.launch();
    const page = await browser.newPage();
    await page.goto(url);
    
    // scrape src content for image links
    const [el] = await page.$x('//*[@id="imgBlkFront"]');
    const src = await el.getProperty('src');
    const imgURL = await scr.jsonValue();
    
    // scrape title of book
    const [el2] = await page.$x('//*[@id="productTitle"]/text()');
    const txt = await el2.getProperty('textContent');
    const title = await txt.jsonValue();

    // scrape price of book
    const [el3] = await page.$x('//*[@id="buyNewSection"]/div/div/span/span');
    const txt2 = await el3.getProperty('textContent');
    const price = await txt2.jsonValue();


    console.log({title, price});

    browser.close();
}


scrapeProduct('https://www.amazon.sg/Black-Swan-Improbable-Robustness-Fragility/dp/081297381X')
```

Content is accessed via XPath. If unsucessful in obtaining data using shorthand Xpath, copy and use the full Xpath.


