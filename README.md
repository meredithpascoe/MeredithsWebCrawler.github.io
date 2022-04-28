# MeredithsWebCrawler.github.io
The web crawler created for this lab collects data from the National Weather Service website. It scrapes data from Ypsilanti, Michigan's seven day forecast page. 

![forcast](img/7day.PNG)

Do carry out this process, one must first import the Requests library and use it to download the webpage. The BeautifulSoup Library also needs to be imported in order to correctly parse the html. 
```python
# Import Requests library 
import requests
# Download webpage using requests.get
page = requests.get("https://forecast.weather.gov/MapClick.php?lat=42.2408&lon=-83.6131#.YmF-q9PMKUk")
# Import BeautifulSoup library and create a class to parse the webpage
from bs4 import BeautifulSoup
soup = BeautifulSoup(page.content, 'html.parser')
```
