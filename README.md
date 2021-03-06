# Supported Local Restaurants in Manitoba
An API that will provide you with general information about restaurants in Manitoba.  

The API will return a list of list of local restaurants (restaurant name, location) for the selected cities. In addition to this, the API can return the opening and closing times of supported restaurants with their city names, restaurant names, and a boolean indicating whether or not they are open at midnight. The APIs can also return a list of supported restaurants including their cuisine types and the city they are in.

## API documentation
Our API is a simple API, which only uses GET requests to access the information. You can perform the GET request at:
```
https://apis.localrestaurant.com
```

## Endpoints and Parameters
The API will have three endpoints, and the information is about the three endpoints within their parameters.
### Restaurant
- **restaurants**: Access to a list of restaurants in the given city and return the list of local restaurants.
  - **parameter**
    - ```id (string)```: id of city. Required.
    - ```Name(string)```: Name of Restaurant. Optional
    - ```Delivery(boolean)```: Indicate if the restaurant deliver or not. Required.
    - ```Version(int)```: Indicates how many copies the user want to get. Optional.

### Time
  - **time**: Access the list of opening and closing times for supported restaurants. You only need to input the city's id, restaurant's name and the boolean condition (true, if looking for restaurants open at midnight). 
  - **parameter**
    - ```id (string)```: id of city with specific time type. Required
      * *For example: "id": "WPG"*
    - ```Name (string)```: Name of the restaurant. Required.
    - ```support_overnight(boolean)```: Boolean to check if the restaurant will be open overnight. Optional.

### Cuisine
  - **cuisine**: Access the list of cuisines of the supported city and return the list of restaurant from that cuisin. You only need to input the cuisine name, city id, version. Required.
  - **parameter**
    - ```id (string)```: The id of the city. Required.
      * *For example: "id":"WPG"* means Winnipeg.
    - ```Name (string)```: The name of the cuisine you want to search. Required.
    - ```Version (int)```: Indicate how many copies it should return. Required.

## Sample requests

* Sample requests if a user wishes to check for a list of restaurants;
  * Browser version -

    ```
    http://apis.localrestaurant.com/restaurants/json?id=WPG&Name=Fion&delivery=true&version=1
    http://apis.localrestaurant.com/restaurants/json?id=WPG
    ```
  * JSON file version -
    ```
    [
        {
          "id": "WPG"
          "Name": "Fion"
          "delivery":true
          "version": 1
      }
    ]
    ```

* Sample requests if a user wishes to check opening and closing times of a restaurant:
  * Browser version -
    ```
    http://apis.localrestaurant.com/Time/json?id=Winnipeg,Manitoba,StandardTime&name=KingHeadPub&support_overnight=false
    http://apis.localrestaurant.com/Time/json?id=Winnipeg,Manitoba,StandardTime&name=KingHeadPub
    ```
  * JSON file version -
    ```
    [
      {
        "Id": "WPG",
        "Name": "King's Head Pub",
        "support_overnight": "false"
      }
    ]
    ```
* Sample requests if a user wishes to check the cuisine types in a city:
  * Browser version -
    ```
    http://apis.localrestaurant.com/Cuisine/json?id=WP&Name=filipinocuisine&version=1
    http://apis.localrestaurant.com/Cuisine/json?id=WP&Name=filipinocuisine
    ```
  * JSON file version -
    ```
    [
        {
          "id": "WPG",
          "Name": "filipino cuisine"
          "version":1
        }
    ]
    ```

  
## Sample response
Sample response in JSON when user want to check for a list of restaurants:
```
{
  "result":
  {
    [
      "Name": "Fion"
      "Location": "1582 Regent Ave"
    ],
    [
      "Name": "Fion"
      "Location": "1180 Grant Avenue"
    ]
  }
  "responses: "200"
}
```
Sample response in JSON when user wishes to check opening and closing times of restaurants in Winnipeg:
```
{
  "result":
  {
    "open"      : "11:00 AM",
    "closing"   : "9:00 PM",
  }
  "responses": "200"
}
```
Sample response in JSON when users wishes to see the list of restaurants in Winnipeg by cuisine type:
```
{
  "result":
  {
    [
      "Name": "Kalan Restaurant"
      "Location": "1449 Arlington St"
    ],
    [
      "Name": "Myrna's Cafe N Catering"
      "Location": "833 Sargent Ave"
    ],
    ...
   }
   "responses":"200"
}
```
## Response code
The "response" in the API will contain the response description of the resquest. There are 2 values in the response message of the API:
- **"200"**: Sucessful operation.
- **"400"**: Invalid input.

## Authors
* [Emily Nguyen](https://github.com/emily0906)
* [Charina Duenas](https://github.com/pandorasjuicebox)
* [Rajinder Singh](https://github.com/rajindersingh751)
* [Mohammed Anjum](https://github.com/vijdan-anjum)

## Acknowledgements
- [Sunrise Sunset](https://sunrise-sunset.org/api)
- [Documenting APIs](https://idratherbewriting.com/learnapidoc/pubapis_openapi_step1_openapi_object.html)
