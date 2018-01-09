# apify-review-scrapers

# About
<p>Apify crawlers with unified input and settings for monitoring of reviews. </p>
<p>You can set behavior and wait for results.</p>
<p>Settings must be placed to "customData" of our crawler as JSON object.</p>

# Modes

```java
{"mode": <mode>}
```
<b>"recheck"</b>
This setting requires to set at least additional ```"url_list"``` parameter(exception for keboola extractor where is possible to import table) which contains list of objects containing at least ```"URL"``` parameter with url of restaurant.

general settings:
```java
{
  "mode": "recheck",
  "url_list": [{"URL": "https://www.tripadvisor.com/Restaurant_Review-g186338-d814048-Reviews-Carluccios_St_Christophers_Place-London_England.html"]
}
```

optional settings:
- contain optional parameters in address objects:
```"cutoff_date"``` -> it scrapes all reviews to the Past before reachng this date - if date is not set -> searching all reviews
```"id"``` -> can be used for your needs, returned after page is scraped - returned as ```"ext_id"```

```java
{
  "mode": "recheck",
  "url_list": [{"URL": "https://www.tripadvisor.com/Restaurant_Review-g186338-d814048-Reviews-Carluccios_St_Christophers_Place-London_England.html", "cutoff_date": "2017-12-9", "id": "any string"}]
}
```

<b>"normal"</b>
This setting requires to set at least additional ```"locations"``` parameter which contains list of START URLS. It will then listing all possible restaurants visible in these locations and it will extract all possible reviews and informations.
```java
{
  "mode": "normal",
  "locations": ["https://www.tripadvisor.com/Restaurants-g186338-London_England.html"]
}
```

<b>"get_urls_only"</b>
This setting requires to set at least additional "locations" parameter which contains list of START URLS. It will then listing all possible restaurants in these locations and return their urls.
```java
{
  "mode": "get_urls_only",
  "locations": ["https://www.tripadvisor.com/Restaurants-g186338-London_England.html"]
}
```

# Disable pagination in reviews
Optional parameter used for !switching off pagination! at reviews. It will override default settings of any mode.
```java
{"pagination": false}
```
