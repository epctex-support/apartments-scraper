# Actor - Apartments Scraper

## Apartments scraper

Since Apartments doesn't provide a proper free API, this actor should help you to retrieve data from it.

The Apartments data scraper supports the following features:

- Scrape any address you would like to get - You can search for a specific location and scrape the results accordingly.

- Apply any of the filters - You can apply any filter that provided by the website.

- Scrape property details - You can target any of the property detail link.

- Limit the results by page or amount of property. - If you don't want to get all the results but a specific amount you can limit it.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/apartments-scraper/issues).

### Incoming Changes

-   Integrate `startPage` field.

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Apartments that should be visited. Possible fields are:

| Field                | Type    | Description                                                                                               |
| -------------------- | ------- | --------------------------------------------------------------------------------------------------------- |
| startUrls            | Array   | (optional) List of Apartments URLs. You should only provide list or property detail URLs                  |
| maxItems             | Integer | (optional) You can limit scraped properties. This should be useful when you search through the big lists. |
| endPage              | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`.                           |
| search               | String  | (optional) Location keyword that you would like to search the properties in.                              |
| proxy                | Object  | Proxy configuration                                                                                       |
| extendOutputFunction | String  | (optional) Function that takes a JQuery handle ($) as argument and returns object with data               |

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use <a href="https://www.apify.com/docs/proxy">Apify Proxy</a>.

### Tip

When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also apply any of the filters to the search results. Go to Apartments.com, search for a location, apply filters and copy/paste the link as **startUrl**.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If actor doesn't block very often it'll scrape 100 listings in 1 minutes with ~0.03-0.04 compute units.

### Apartments Scraper Input example

```json
{
    "startUrls": [
        "https://www.apartments.com/sobe-apartment-rentals-miami-beach-fl/26xc7jb/",
        "https://www.apartments.com/apartments/miami-fl/student-housing/",
        "https://www.apartments.com/?sk=544b92fe1f766950d57299dc624e9ff9&bb=0nijpwq7qH0t1s0oB"
    ],
    "search": "new york",
    "proxy": {
        "useApifyProxy": true
    },
    "endPage": 1,
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
  "id": "26xc7jb",
  "propertyName": "SoBe Apartment Rentals",
  "url": "https://www.apartments.com/sobe-apartment-rentals-miami-beach-fl/26xc7jb",
  "breadcrumbs": [
    "Home",
    "Florida",
    "Miami Beach",
    "SoBe Apartment Rentals"
  ],
  "location": {
    "fullAddress": "907-911 Euclid Ave Miami Beach FL 33139",
    "state": "Florida",
    "city": "Miami Beach",
    "neighborhood": "Flamingo",
    "postalCode": "33139",
    "streedAddress": "907-911 Euclid Ave"
  },
  "coordinates": {
    "latitude": 25.77973,
    "longitude": -80.13479
  },
  "rating": null,
  "isVerified": true,
  "rent": {
    "min": 1100,
    "max": 1750
  },
  "beds": "Studio - 2 bd",
  "baths": "1 - 2 ba",
  "sqft": "550 - 1,250 sq ft",
  "transitAndPOI": [
    {
      "name": "Strip Center at 915-943 Washington Ave",
      "drive": "3 min",
      "distance": "0.1 mi"
    },
    {
      "name": "Strip Center at 124 11th St",
      "drive": "8 min",
      "distance": "0.4 mi"
    },
    {
      "name": "Strip Center at 901-917 Alton Rd",
      "drive": "8 min",
      "distance": "0.4 mi"
    },
    {
      "name": "Jungle Island",
      "drive": "8 min",
      "distance": "3.4 mi"
    },
    {
      "name": "Miami Children's Museum",
      "drive": "9 min",
      "distance": "3.9 mi"
    },
    {
      "name": "Miami Seaquarium",
      "drive": "22 min",
      "distance": "11.2 mi"
    },
    {
      "name": "Virginia Key Beach and Park",
      "drive": "23 min",
      "distance": "11.4 mi"
    }
  ],
  "scores": {
    "walkScore": 95,
    "transitScore": 53
  },
  "neighborhoodDescription": "Flamingo, also known as Flamingo/Lummus, is a vibrant neighborhood situated right in the heart of South Beach. Residents enjoy easy beach access along with plenty of exceptional restaurants, bars, museums, art galleries, shops, and the famous Art Deco Historic District. Flamingo is also adjacent to fantastic shopping on Lincoln Road.\n                        Aside from its many exciting metropolitan amenities, Flamingo offers two lush parks for residents and visitors alike to enjoy—Flamingo Park and Lummus Park. Flamingo’s prime location sits within countless additional attractions in the rest of Miami Beach as well as Downtown Miami, Brickell, and Wynwood. Getting around from Flamingo is simple with convenience to the MacArthur Causeway and I-195.\n                \n                \n                    Learn More About Flamingo",
  "schools": {
    "public": [
      {
        "type": "Public Elementary & Middle School",
        "name": "Fienberg/Fisher K-8 Center",
        "grades": "PK-8",
        "numberOfStudents": "869"
      },
      {
        "type": "Public Middle School",
        "name": "Nautilus Middle School",
        "grades": "6-8",
        "numberOfStudents": "1,032"
      },
      {
        "type": "Public High School",
        "name": "Miami Beach Senior High School",
        "grades": "9-12",
        "numberOfStudents": "2,340"
      }
    ],
    "private": [
      {
        "type": "Private Elementary, Middle & High School",
        "name": "Landow Yeshiva Center",
        "grades": "PK-12",
        "numberOfStudents": ""
      },
      {
        "type": "Private Middle & High School",
        "name": "Congregation Beth Medrash Levi",
        "grades": "7-12",
        "numberOfStudents": "90"
      }
    ],
    "colleges": [
      {
        "name": "AI Miami International University of Art and Design",
        "drive": "AI Miami International University of Art and Design",
        "distance": "4.6 mi"
      },
      {
        "name": "Miami Dade College",
        "drive": "Miami Dade College",
        "distance": "5.4 mi"
      },
      {
        "name": "University of Miami",
        "drive": "University of Miami",
        "distance": "11.5 mi"
      }
    ]
  },
  "fees": [
    {
      "title": "Pet Policies (Pets Negotiable)",
      "policies": [
        {
          "header": "Dogs Allowed",
          "values": [
            {
              "key": "Weight limit",
              "value": "40 lb"
            },
            {
              "key": "Pet interview",
              "value": "Not required"
            },
            {
              "key": "Spayed/Neutered",
              "value": "Not required"
            },
            {
              "key": "Declawed",
              "value": "Not required"
            },
            {
              "key": "One time Fee",
              "value": "$250"
            }
          ]
        },
        {
          "header": "Cats Allowed",
          "values": [
            {
              "key": "Pet interview",
              "value": "Not required"
            },
            {
              "key": "Spayed/Neutered",
              "value": "Not required"
            },
            {
              "key": "Declawed",
              "value": "Required"
            },
            {
              "key": "One time Fee",
              "value": "$250"
            }
          ]
        }
      ]
    },
    {
      "title": "Fees",
      "policies": [
        {
          "header": "Parking",
          "values": [
            {
              "key": "Street",
              "value": ""
            }
          ]
        },
        {
          "header": "Other Fees",
          "values": [
            {
              "key": "Application Fee",
              "value": "$100"
            }
          ]
        }
      ]
    },
    {
      "title": "Details",
      "policies": [
        {
          "header": "Utilities Included",
          "values": [
            {
              "key": "Gas",
              "value": ""
            },
            {
              "key": "Water",
              "value": ""
            },
            {
              "key": "Trash Removal",
              "value": ""
            },
            {
              "key": "Sewer",
              "value": ""
            }
          ]
        },
        {
          "header": "Property Information",
          "values": [
            {
              "key": "Built in 1936",
              "value": ""
            },
            {
              "key": "16 units/2 stories",
              "value": ""
            },
            {
              "key": "Furnished",
              "value": ""
            }
          ]
        }
      ]
    }
  ],
  "description": "About SoBe Apartment Rentals\n                        Welcome to South Beach Rental Apartments, where you can find an affordable luxury apartment. Our leasing specialists will show you a variety of apartments in your price range. We have full service buildings with full service amenities. We accept pets. We will work with all credit situations. Let South Beach Rental Apartments find your new home and make your move a more pleasurable experience. *Prices Subject to Change Based on Availability*\n\n                SoBe Apartment Rentals is an apartment located in Miami/Dade County, the 33139 ZIP Code, and the Miami-Dade attendance zone.",
  "amenities": [
    {
      "title": "Community Amenities",
      "value": [
        "Pool",
        "Fitness Center",
        "Laundry Facilities",
        "Furnished Units Available",
        "Laundry Facilities",
        "Maintenance on site",
        "Furnished Units Available",
        "Elevator",
        "Fitness Center",
        "Pool",
        "Gated",
        "Sundeck",
        "Grill",
        "Picnic Area"
      ]
    },
    {
      "title": "Apartment Features",
      "value": [
        "Air Conditioning",
        "Dishwasher",
        "High Speed Internet Access",
        "Hardwood Floors",
        "High Speed Internet Access",
        "Air Conditioning",
        "Heating",
        "Ceiling Fans",
        "Tub/Shower",
        "Dishwasher",
        "Kitchen",
        "Range",
        "Refrigerator",
        "Hardwood Floors",
        "Tile Floors",
        "Den",
        "Walk-In Closets",
        "Balcony",
        "Yard",
        "Garden"
      ]
    }
  ],
  "contact": {
    "phone": "+1-786-623-5446",
    "logo": "https://images1.apartments.com/i2/MzLghRW57B06n9LwsCwa86cNW9bM-0BifS3NxF7_nxs/115/renters-paradise-realty-inc-logo.jpg",
    "name": ""
  },
  "models": [
    {
      "modelName": "Studio",
      "rentLabel": "$1,100 – $1,200",
      "details": [
        "Studio",
        "1 bath",
        "550 sq ft",
        "$1,200 deposit"
      ],
      "leaseOptions": "$1,200 deposit",
      "availability": "1 Available unit",
      "units": [
        {
          "type": "Unit 10",
          "price": "$1,100",
          "sqft": "550",
          "availability": "Soon"
        }
      ]
    },
    {
      "modelName": "1 Bed/1 Bath",
      "rentLabel": "$1,200 – $1,300",
      "details": [
        "1 bed",
        "1 bath",
        "685 – 875 sq ft",
        "12 Month Lease",
        "Available Soon"
      ],
      "leaseOptions": "12 Month Lease,\n\t\t\t\t\t\t\t\tAvailable Soon",
      "availability": "",
      "units": []
    },
    {
      "modelName": "1 Bed/1 Bath",
      "rentLabel": "$1,300",
      "details": [
        "1 bed",
        "1 bath",
        "700 sq ft",
        "$1,300 deposit"
      ],
      "leaseOptions": "$1,300 deposit",
      "availability": "1 Available unit",
      "units": [
        {
          "type": "Unit 9",
          "price": "$1,300",
          "sqft": "700",
          "availability": "Soon"
        }
      ]
    },
    {
      "modelName": "2 Bed/2 Bath",
      "rentLabel": "$1,600 – $1,750",
      "details": [
        "2 beds",
        "2 baths",
        "1,100 – 1,250 sq ft",
        "12 Month Lease",
        "Available Soon"
      ],
      "leaseOptions": "12 Month Lease,\n\t\t\t\t\t\t\t\tAvailable Soon",
      "availability": "",
      "units": []
    }
  ],
  "scrapedAt": "2021-11-27T12:04:06.752Z",
  "photos": [
    "https://images1.apartments.com/i2/cS0Cu8ytY9zn8aI0V3DcsPiSca-7KgPPd-tOowXs5Uw/111/sobe-apartment-rentals-miami-beach-fl-primary-photo.jpg?p=1",
    "https://images1.apartments.com/m2/ogrZ5C9tUeyJJw1Rg_NLfNm3O6sorfEMC1OyLLDgLko/H330W495/sobe-apartment-rentals-miami-beach-fl-map-image-of-the-property.jpg?p=1",
    "https://images1.apartments.com/i2/xhlEsuSaTc0Oc7ZA8jNyLrpMwmkgkgE3jW9WzfJJ0bM/117/sobe-apartment-rentals-miami-beach-fl-building.jpg?p=1",
    "https://images1.apartments.com/i2/PGbG-MlQgqD0TytUnv7fuU0nlSDJJqx8_-MoePj0CcA/117/sobe-apartment-rentals-miami-beach-fl-bedroom.jpg?p=1",
    "https://images1.apartments.com/i2/DG2gCa0vZy9JTfjuvPmv23hFqCIVh-iEYiQyd5vxpx8/117/sobe-apartment-rentals-miami-beach-fl-bedroom.jpg?p=1"
  ]
}
```
