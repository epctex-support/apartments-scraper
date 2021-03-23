# Actor - Apartments Scraper

## Apartments scraper

Since Apartments doesn't provide a proper free API, this actor should help you to retrieve data from it.

The Apartments data scraper supports the following features:

- Scrape any address you would like to get - You can search for a specific location and scrape the results accordingly.

- Apply any of the filters - You can apply any filter that provided by the website.

- Scrape property details - You can target any of the property detail link.

- Limit the results by page or amount of property. - If you don't want to get all the results but a specific amount you can limit it.


## Bugs, fixes, updates and changelog
This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/tugkan/apartments-scraper/issues).

### Incoming Changes
- Retrieve all the photos of a property.
- Integrate `startPage` field.
- Scrape better contact, vendor and agent names.
- Scrape more information that can be retrieved from detail pages. If you have any requests please request it from [here](https://github.com/tugkan/apartments-scraper/issues).


## Input Parameters

The input of this scraper should be JSON containing the list of pages on Apartments that should be visited. Required fields are:

| Field | Type | Description |
| ----- | ---- | ----------- |
| startUrls | Array | (optional) List of Apartments URLs. You should only provide list or property detail URLs |
| search | String | (optional) Location keyword that you would like to search the properties in. |
| endPage | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`. |
| maxItems | Integer | (optional) You can limit scraped properties. This should be useful when you search through the big lists.|
| proxy | Object | Proxy configuration |
| extendOutputFunction | String | (optional) Function that takes a JQuery handle ($) as argument and returns object with data |
This solution requires the use of **Proxy servers**, either your own proxy servers or you can use <a href="https://www.apify.com/docs/proxy">Apify Proxy</a>.

##### Tip
When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also apply any of the filters to the search results. Go to Apartments.com, search for a location, apply filters and copy/paste the link as **startUrl**.

### Compute Unit Consumption
The actor optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If actor doesn't block very often it'll scrape 100 listings in 1 minutes with ~0.03-0.04 compute units.

### Apartments Scraper Input example
```json

{
  "startUrls":[
    {"url":"https://www.apartments.com/sobe-apartment-rentals-miami-beach-fl/26xc7jb/"},
    {"url":"https://www.apartments.com/apartments/miami-fl/student-housing/"}
  ],
  "proxy":{
    "useApifyProxy":true
  },
  "endPage":1,
  "maxItems": 100
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Apartments Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Apartments actor.

## Scraped Apartments Properties
The structure of each item in Apartments listings looks like this:

###Property Output

```json
{
  "id": "fbt1sms",
  "propertyName": "Advenir at Biscayne Shores",
  "url": "https://www.apartments.com/advenir-at-biscayne-shores-miami-fl/fbt1sms/",
  "breadcrumbs": [
    "Home",
    "Florida",
    "Miami",
    "Advenir at Biscayne Shores"
  ],
  "location": {
    "fullAddress": "12016 NE 16th Ave Miami FL 33161",
    "state": "Florida",
    "city": "Miami",
    "neighborhood": "Miami",
    "postalCode": "33161",
    "streedAddress": "12016 NE 16th Ave"
  },
  "rating": 4,
  "isVerified": true,
  "rent": {
    "min": 1545,
    "max": 1855
  },
  "beds": "1 - 3 bd",
  "baths": "1 - 2 ba",
  "sqft": "733 - 1,319 sq ft",
  "transitAndPOI": [
    {
      "name": "Johnson & Wales University, Florida Campus",
      "drive": "4 min",
      "distance": "0.8 mi"
    },
    {
      "name": "Barry University",
      "drive": "9 min",
      "distance": "2.9 mi"
    },
    {
      "name": "Florida International University",
      "drive": "11 min",
      "distance": "3.9 mi"
    },
    {
      "name": "Golden Glades",
      "drive": "14 min",
      "distance": "5.8 mi"
    },
    {
      "name": "Opa-Locka",
      "drive": "17 min",
      "distance": "6.7 mi"
    },
    {
      "name": "Strip Center at 11806-11890 Biscayne Blvd",
      "drive": "4 min",
      "distance": "0.2 mi"
    },
    {
      "name": "123rd Street Plaza",
      "drive": "5 min",
      "distance": "0.2 mi"
    },
    {
      "name": "Strip Center at 1677-1697 NE 123rd St",
      "drive": "6 min",
      "distance": "0.3 mi"
    },
    {
      "name": "Enchanted Forest Elaine Gordon Park",
      "drive": "4 min",
      "distance": "1.2 mi"
    },
    {
      "name": "Arch Creek Park & Nature Center",
      "drive": "4 min",
      "distance": "1.3 mi"
    },
    {
      "name": "Oleta River State Park",
      "drive": "11 min",
      "distance": "3.4 mi"
    },
    {
      "name": "Greynolds Park",
      "drive": "10 min",
      "distance": "4.0 mi"
    },
    {
      "name": "Jungle Island",
      "drive": "22 min",
      "distance": "9.7 mi"
    },
    {
      "name": "Miami International",
      "drive": "33 min",
      "distance": "15.2 mi"
    },
    {
      "name": "Fort Lauderdale–Hollywood International",
      "drive": "29 min",
      "distance": "15.3 mi"
    }
  ],
  "scores": {
    "walkScore": 88,
    "transitScore": 0
  },
  "neighborhoodDescription": "Located in the heart of southeastern Florida, Miami is a vibrant city with a distinct international appeal. Miami’s diversity is evident in its many neighborhoods, from the artistic allure of Wynwood and the financial prowess of Brickell to the dance halls of Little Havana and the tranquil vibe of Coconut Grove. Downtown Miami is at the city’s core, boasting the third-tallest skyline in the U.S. alongside the picturesque Biscayne Bay.\n                        \nMiami’s rental options are also incredibly diverse, from luxury apartments and beachfront condos in the city center to cozy townhomes and spacious houses in the suburbs. Miami offers plenty to do outside the home. Residents and visitors alike enjoy perusing the extensive exhibits at the Perez Art Museum, Frost Museum of Science, Miami Children’s Museum, and Vizcaya Museum and Gardens. Miami loves their sports, cheering on the MLB Marlins at Marlins Park, NBA Heat at American Airlines Arena, and NFL Dolphins at Hardrock Stadium in Miami Gardens.",
  "schools": {
    "public": [
      {
        "type": "Public Elementary & Middle School",
        "name": "David Lawrence Jr. K-8 Center",
        "grades": "Grades PK-8",
        "numberOfStudents": "1,507 Students",
        "schoolPhone": "(305) 354-2600"
      },
      {
        "type": "Public Middle School",
        "name": "North Miami Middle School",
        "grades": "Grades 6-8",
        "numberOfStudents": "945 Students",
        "schoolPhone": "(305) 891-5611"
      },
      {
        "type": "Public High School",
        "name": "North Miami Senior High School",
        "grades": "Grades 9-12",
        "numberOfStudents": "2,464 Students",
        "schoolPhone": "(305) 891-6590"
      },
      {
        "type": "Public High School",
        "name": "Alonzo And Tracy Mourning Senior High Biscayne Bay Campus",
        "grades": "Grades 9-12",
        "numberOfStudents": "1,699 Students",
        "schoolPhone": "(305) 919-2000"
      }
    ],
    "private": [
      {
        "type": "Private Elementary School",
        "name": "El Shaddai School",
        "grades": "Grades K-3",
        "numberOfStudents": "",
        "schoolPhone": "(305) 891-8966"
      },
      {
        "type": "Private Elementary, Middle & High School",
        "name": "Montessori School Of North Miami",
        "grades": "Grades K-12",
        "numberOfStudents": "",
        "schoolPhone": "(305) 893-5994"
      },
      {
        "type": "Private Elementary, Middle & High School",
        "name": "Montessori School Of North Miami",
        "grades": "Grades K-12",
        "numberOfStudents": "",
        "schoolPhone": "(305) 893-5994"
      },
      {
        "type": "Private Elementary School",
        "name": "Von Wedel Montessori School",
        "grades": "Grades PK-2",
        "numberOfStudents": "135 Students",
        "schoolPhone": "(954) 473-4400"
      }
    ]
  },
  "fees": {
    "oneTimeFees": {
      "Admin Fee": "$325",
      "Application Fee": "$125",
      "Cat Fee": "$500",
      "Dog Fee": "$500"
    },
    "monthlyFees": {
      "Cat Rent": "$25",
      "Dog Rent": "$25"
    }
  },
  "description": "About Advenir at Biscayne Shores\n                Surround yourself in convenience and comfort at Advenir At Biscayne Shores Apartments in North Miami, FL. Our premier apartment homes offer convenient location combined with unmatched community amenities and luxurious apartment features that will create the perfect home for your lifestyle! Advenir at Biscayne Shores Apartments enjoys a premier location right on Biscayne Boulevard with immediate access to major highways and roads, great shopping malls, a host of restaurants and many other entertainment and recreational options to choose from.\n\n                \n                    \n                        View Property Website",
  "amenities": [
    {
      "title": "Unique Features",
      "value": [
        "Granite countertop",
        "Individual Climate Control",
        "Outdoor Grills",
        "Pet Friendly",
        "Walk in Closet",
        "Washer/Dryer"
      ]
    },
    {
      "title": "Pet Policy",
      "value": [
        "Comments: Dog",
        "$25 Monthly Pet Rent",
        "$500 Fee",
        "150 lb Weight Limit",
        "2 Pet Limit",
        "Comments: Cat",
        "$25 Monthly Pet Rent",
        "$500 Fee",
        "50 lb Weight Limit",
        "2 Pet Limit"
      ]
    },
    {
      "title": "Parking",
      "value": []
    },
    {
      "title": "Property Information",
      "value": [
        "Built in 2013",
        "240 Units/3 Stories"
      ]
    },
    {
      "title": "Lease Length",
      "value": [
        "7 months, 9 months, 12 months, 15 months"
      ]
    },
    {
      "title": "Interior",
      "value": [
        "Business Center",
        "Clubhouse"
      ]
    },
    {
      "title": "Fitness & Recreation",
      "value": [
        "Fitness Center",
        "Pool"
      ]
    },
    {
      "title": "Features",
      "value": [
        "High Speed Internet Access",
        "Washer/Dryer - In Unit",
        "Air Conditioning",
        "Heating"
      ]
    },
    {
      "title": "Kitchen",
      "value": [
        "Dishwasher",
        "Granite Countertops",
        "Range"
      ]
    },
    {
      "title": "Living Space",
      "value": [
        "Walk-In Closets"
      ]
    }
  ],
  "contact": {
    "phone": "833-683-3245833-683-3245",
    "name": "Office Hours At Advenir at Biscayne Shores"
  },
  "models": [
    {
      "floorPlan": "https://images1.apartments.com/i2/7k8cKcd43n4N5ilGGuFK0O9_Rprd9BsFHMxqEtvqwZE/117/advenir-at-biscayne-shores-miami-fl-alhambra.jpg?p=1",
      "modelName": "Alhambra",
      "rentLabel": "$1,545 – $1,855",
      "details": [
        "1 bed",
        "1 bath",
        "733 sq ft",
        "$450 Deposit"
      ],
      "leaseOptions": "$450 Deposit",
      "availability": "3 Available units",
      "units": [
        {
          "type": "Unit 07-104",
          "price": "$1,545",
          "sqft": "733",
          "availability": "Now"
        },
        {
          "type": "Unit 04-307",
          "price": "$1,570",
          "sqft": "733",
          "availability": "Now"
        },
        {
          "type": "Unit 05-106",
          "price": "$1,705",
          "sqft": "733",
          "availability": "Now"
        }
      ]
    },
    {
      "floorPlan": "https://images1.apartments.com/i2/rk5cDeh5L3NS56wrtxzl2cH7gRjLiBCArn7ii4U2S7g/117/advenir-at-biscayne-shores-miami-fl-biscayne.jpg?p=1",
      "modelName": "Biscayne",
      "rentLabel": "Call for Rent",
      "details": [
        "2 beds",
        "2 baths",
        "1,045 sq ft",
        "$450 Deposit"
      ],
      "leaseOptions": "$450 Deposit",
      "availability": "Not Available",
      "units": []
    },
    {
      "floorPlan": "https://images1.apartments.com/i2/YIfbdr284QhkY7JjBZj-YHY1jOfnoxiye5WhH7374yI/117/advenir-at-biscayne-shores-miami-fl-cordova.jpg?p=1",
      "modelName": "Cordova",
      "rentLabel": "Call for Rent",
      "details": [
        "3 beds",
        "2 baths",
        "1,319 sq ft",
        "$450 Deposit"
      ],
      "leaseOptions": "$450 Deposit",
      "availability": "Not Available",
      "units": []
    }
  ],
  "scrapedAt": "2021-03-20T21:12:39.633Z",
  "photos": [
    "https://images1.apartments.com/i2/EINbwwVCywBvRzfr0wOeSNFQ6jSQJc4UezLuLO52rS4/111/advenir-at-biscayne-shores-miami-fl-open-concept-layout-living-room-and-kitc.jpg?p=1",
    "https://images1.apartments.com/i2/HDQ2izk8FCyQ0-8Fq2Ck0bQTwCc-Y4HgzWPjuyQwgv0/117/advenir-at-biscayne-shores-miami-fl-fully-equipped-kitchen-with-oven-range-a.jpg?p=1",
    "https://images1.apartments.com/i2/ejnF5a-RJCOTbORTa08V-HuRKeqAZPzUpx9HRjTChPA/117/advenir-at-biscayne-shores-miami-fl-fully-equipped-kitchen-with-dishwasher-o.jpg?p=1",
    "https://images1.apartments.com/i2/OFRv1Hy3RBPenUYtmgQJ29EkZQAkqCmlMeH5KsPIjz0/117/advenir-at-biscayne-shores-miami-fl-fully-equipped-kitchen-with-dishwasher-o.jpg?p=1",
    "https://images1.apartments.com/i2/WCeNeGB-eE1pKScjrHbd6V58pyMcviN3Bo4aS1NRrQ0/117/advenir-at-biscayne-shores-miami-fl-fully-equipped-kitchen-with-oven-range-a.jpg?p=1"
  ]
}
```
