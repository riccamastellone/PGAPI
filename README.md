# PGAPI
http://www.paginegialle.it/

These are the API to access the Italian Pagine Gialle. 

###Installation
 - Download and extract the archive
 - `composer install`
 
####Requirements
- PHP >= 5.4<br>
- The package uses the microframework flight (http://flightphp.com/) that works with both Apache and Nginx. The version that you are going to install, available in this package, is designed for Apache but tou can change it for Nginx<br>
- Permission to write to the folder `Cookies/` 

###Using
When the package is installed you can access the API as you are more comfortable, or using it as external server or internal the script.
<br>
Consider bees installed at the following URL: http://your_url.dom. The primitives available are the following: <br>
<b> -http://your_url.dom/number/number%20to%20search: </b> where "number%20to%20search" is the phone number encoded using url encoding (spaces are allowed) <br>
<b> -http://your_url.dom/company/company%20to%20search: </b> where "company%20to%20search" is the name of the encoded through url encoding (spaces are allowed) <br>
<b> -http://your_url.dom/place/restricted%20area: </b> where "restricted%20area" is the geographical area to which restrict your search encoded trough url encoding (spaces are allowed). Allowed all postal addresses, zip codes, provinces, municipalities, regions, even fractions specifying the province. You can not use the geolocation. <br>
<b> -http://your_url.dom/company/company%20to%20search/place/restricted%20area: </b> where "company%20to%20search" is the name of the company encoded through url encoding (are allowed the spaces) and "restricted%20area" is the geographical area that restrict your search encoded by url encoding (spaces are allowed) to use it as referring to the previous point <br>
<b> -http://your_url.dom/category/0000000000: </b> where "0000000000" is the number of the category of the corresponding companies. You can get this number from a previous response on another search <br>
<b> -http://your_url.dom/search/term%20to%20search: </b> where "term%20to%20search" is a generic research encoded using url encoding (spaces are allowed) <br>

###Response

```JSON
{
    "result": [
        {
            "name": "...",
            "subtitle": "..." | "" | null,
            "description": "..." | null,
            "image": "..." | null,
            "place": {
                "address": "..." | null,
                "postal-code": "..." | null,
                "locality": "..." | null,
                "region": "..." | null,
                "state": "..." | null,
                "latitude": "..." | null,
                "longitude": "..." | null
            },
            "telephone": "..." | null,
            "website": "..." | null,
            "category": "...",
            "category-number": "..."
        },
        {
            ...
        }
    ],
    "status": "OK" | "ERROR",
    "length": ...,
    "source": "http:\/\/www.paginegialle.it\/ricerca\/...",
    "query": "...",
    "nextPage": null
}
```
**NOTE**
If an error will overtake the status changes from `OK` to `ERROR`.
`nextPage` contains the url to retrieve the next set of results
