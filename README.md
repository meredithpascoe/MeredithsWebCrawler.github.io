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
The next step is to capture all the extended forecast items from the html. Following this, one is able to find all the time period names as well as the weather conditions summary, temperature, and conditions description used in the seven day forecast. 
```python
# Capture all the extended forecast items 
seven_day = soup.find(id="seven-day-forecast")
forecast_items = seven_day.find_all(class_="tombstone-container")

# Find all the time period names used in the seven day forecast
period_tags = seven_day.select(".tombstone-container .period-name")
periods = [pt.get_text() for pt in period_tags]
periods

# Find the weather conditions summary, temperature, and and conditions description for the various time periods in the seven day forecast
short_descs = [sd.get_text() for sd in seven_day.select(".tombstone-container .short-desc")]
temps = [t.get_text() for t in seven_day.select(".tombstone-container .temp")]
descs = [d["title"] for d in seven_day.select(".tombstone-container img")]
print(short_descs)
print(temps)
print(descs)
```
