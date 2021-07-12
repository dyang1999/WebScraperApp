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
