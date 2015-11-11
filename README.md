## Data Rep and Querying Project 2015
Student Name: Shane Carville

## Introduction
This project provides the design and documentation for the dataset "Galway City Playgrounds" which is available at [data.gov.ie](https://data.gov.ie/dataset/galway-city-playground-locations). The purpose of this project is to create an API that can be useful to the intended audience and is also easy to use.

##About the Data
This dataset is about the Galway City playgrounds. This dataset was found at the previously mentioned URL, in Comma Separated Values (CSV) format, and was downloaded from [*data.gov.ie*](https://data.gov.ie/dataset/galway-city-playground-locations/resource/b81820b4-dd2e-4181-b93b-d2033a9f9a85).
The CSV file has 31 rows, with the first being the header or id of the column
There are fifteen values on each line, though some are not as useful as others I have selected the most useful for the user.

Attribute | Description |
---------|--:|------------|----------
**Name** | The name of the playground |
**Location** | The location of the playground |
**Surface** | The type of surface at the playground |
**Parking** | If the playground has parking or not |
**Opening Hours** | The opening hours of the playground |
**Toitlet Facilities** | If the playground has toilets or not |
**Equipment** | If the playgroud has any specilised equipment e.g basketball courts |
**Latitude** | The latitude postion of the playground |
**Longitude** | The longitude postion of the playground |
**Special Needs** | If the playground has access and is suitable for childern with special needs |

The longitude and latitude of the playgrounds could be used in conjuncture with a maps API to give a presise location or just give the co-ordinates and allow the user to enter them into an app.
The opening hours attribute could also be used in conjuncture with another API to check if they park is still open at the time the user queries the dataset.

## Users of the Dataset
> - *Parents*
> - *Baby Sitters*
> - *Schools on a trip*
> - *County Council*

These are just a few examples of users of the dataset.Parents and baby sitters to find their local playground, schools to take kids to after a trip and the county council to see where the current playgrounds are and where they should place the next one if needed. As the API is intended to be used by the general public I feel as though it would be easier for them if the code and the understanding of the API was quite simple.

## Commands for the Dataset

These are the commands that the dataset will respond to.

1. **GET**: Used to query the dataset for a specific an item or ID.
2. **PUT**: Used to add a new row with the appropiate attributes.
3. **POST**: Used to send data to the dataset.
4. **DELETE**: Used to remove a row or attribute in the dataset.

##URLs the Dataset Uses

These are a few of the URls that the dataset will use and what they return.

1. *http://GCityPlaygrounds.com/Mervue*
This will return all playgrounds in the Mervue area.
2. *http://GCityPlaygrounds.com/Mervue/Parking*
This will return what kind of parking the Mervue playground has.
3. *http://GCityPlaygrounds.com/facilities/Mervue*
This will return the facilities available at the Mervue e.g: the toilets and the extra equipment available there.
4. *http://GCityPlaygrounds.com/Preciseloc/Mervue*
This will return the presise location of the playground using the longitude and latitude.
5. *http://GCityPlaygrounds.com/Mervue/extras*
This will return the the extra information on the playground like the type of surface and if the playground caters to childern with special needs.

##  Querying the Dataset

The following is an example of how to use the URLs in the API to query a specific item or ID in the dataset for this example I will show the getting the location

```
You can *get* the location of the playground using the **GET** method at the following URL:
*http://GCityPlaygrounds.com/location/[location]*
where you swap [location] with a town e.g Claddagh.
For example, the URL:
*http://GCityPlaygrounds.com/location/Claddagh*
this will return the list of playgrounds in the Claddagh area.
The data will be returned in JSON format, with the following properties for the playground:
    - *location*: the location of the playground.
    - *parking*: the parking facilities at the playground.
    ...
An example of a response would be:
    ```json
    [ {"location": "Claddagh, Galway", "parking": "Adjacent public car", ...}, {...}, ...]
    ```
```


To get the precise location of the playground using longitude and latitude the URL example is as follows
```
Again using the **GET** method at the following URL
**http://GCityPlaygrounds.com/preciseLoc/[location]*
where [location] is swapped with the location e.g Claddagh.
Example URL
**http://GCityPlaygrounds.com/preciseLoc/Claddagh*
this will then return the percise location of the playgrounds in the Claddagh area.
the data will again be returned in JSON format:
    ``` json
    [ {"longituide": "-9.053", "latitude": "53.267" "location": "Claddagh, Galway",...}, {...}, ...]
    ```
```


The last example is for querying the surface of the playground, the toilet facilities, the equipment there and the playground opening hours and if it caters to childern with special needs.
```
Again using the **GET** method at the following URL
**http://GCityPlaygrounds.com/[location]/facilitles*
where location is swapped with the location e.g Claddagh.
Example URL
**http://GCityPlaygrounds.com/Claddagh/facilitles*
this will then return the percise location of the playgrounds in the Claddagh area.
the data will again be returned in JSON format:
    ``` json
    [ {Claddagh, Galway:, "Toilets:", "No", "Equipment:", "No Special Equipment", "Surface:", "Rubber Wet-pour surface", "Special Needs:", "Yes" }, {...}, ...]
    ```
```

##Maintaining the Dataset

If a user would like to send an image of the playground to the API that could be done using the **POST** request.
As follows:
```
jQuery.post( *http://GCityPlaygrounds.com/Mervue*, [data], success, json );
Replaceing [data] with the data or image that you would like to send to the dataset if successful the success function will return from the code.
```

If the user would like to *ADD* any extra playgrounds or another attriubte to a playground this could be done using the **PUT** request.
As follows:
```
Mervue.dataset('Surface', "Concrete");
This will replace the surface type that is already there with the new type concrete.
```

If the user would like to *remove* any playground or a current atturibute of a playground that could be done using the **DELETE** request.
As follows:
```
( "Mervue" ).removeData( "Equipment", "Basketball courts" );
This will remove the basketball courts attribute in the Equipment column.
```

##Further Links

A link to an API for playground in galway county is available from [Galway County Playground](https://data.gov.ie/dataset/playgrounds-county-galway)

A link to understandind HTTP methods is availavle at the following [Understanding HTTP Methods](http://www.tutorialspoint.com/http/http_methods.htm)
