FORMAT: 1A
HOST: http://dev.mogoapp.co/api

# Mogo API

## Authorization
API will require the `X-Auth-Token` HTTP header.

```http
X-Auth-Token: vr5HmMkzlxKE70W1y4MibiJUusZwZC25NOVBEx3BD1
```

# Group Users

## Login with Email [/login] 

### Post Login with Email [POST]

+ Request (application/json)

      + Body

            {
                "email": "example@gmail.com",
                "password": "123456"
            }

    
+ Response 200 (application/json)

        {
            "data": [
                "id": 1,
                "fullname": "Fanz",
                "email": "kennyfans999@gmail.com",
                "avatar": null,
                "token": "4b4e860edbc82e14506561ad730e2c589e712311"
            ]
        }

## Login with Facebook [/login/facebook] 

### Post Login with Facebook [POST]

+ Request (application/json)

      + Body

            {
                "token": "EAAJCKYTYO1QBAJMRoZBzJYr6ZC54mDNFDrOwOOLYB0j4HtlUTLZA7Rhc3DQ93XmUvo2VcKgSZCxD5GP4iScW7aoi8zpjLQRZArmggQ9rmDr9MUkNHNvuThgMAM77lfLajZAZBnKCGTM0MGboDIhs0msBPrDvgkM86rreKZBCi4uAuGFjTLtrgfZBK"
            }

+ Response 200 (application/json)

        {
            "data": [
                "id": 1,
                "fullname": "null",
                "email": "null",
                "avatar": "null",
                "token": "4b4e860edbc82e14506561ad730e2c589e712311"
            ]
        }


## Register with Email [/register] 

### Post Register with Email [POST]

+ Request (application/json)

      + Body

            {
                "email": "example@gmail.com",
                "plainPassword": "123456",
                "fullname" : "Batman",
                "phone" : "0909999999",
                "address" : "SG"
            }

    
+ Response 200 (application/json)

        {
            "data": [
                "id": 1,
                "fullname": "Batman",
                "email": "example@gmail.com",
                "avatar": null,
                "token": "4b4e860edbc82e14506561ad730e2c589e712311"
            ]
        }

## Check email exist [/check-email] 

### Post Check email exist [POST]

+ Request (application/json)

      + Body

            {
                "email": "example@gmail.com"
            }

    
+ Response 200 (application/json)

        {
            "message": {
                "type": "success",
                "code": 1000,
                "msg": "You can use this email !"
            }
        }

+ Request (application/json)

      + Body

            {
                "email": "example@gmail.com"
            }


+ Response 200 (application/json)

        {
            "message": {
                "type": "error",
                "code": 1001,
                "msg": "Email already exist !"
            }
        }

## Check phone number exist [/check-phone] 

### Post Check phone number exist [POST]

+ Request (application/json)

      + Body

            {
                "phone": "090999999999"
            }

    
+ Response 200 (application/json)

        {
            "message": {
                "type": "success",
                "code": 1000,
                "msg": "You can use this phone number !"
            }
        }

+ Request (application/json)

      + Body

            {
                "phone": "090999999999"
            }


+ Response 200 (application/json)

        {
            "message": {
                "type": "error",
                "code": 1001,
                "msg": "Phone number already exist !"
            }
        }


# Group places
Search and manage places.

## places List [/places{?people,sortBy,priceFrom,priceTo,rating,cuisine,hasDiscount,lat,long,number}]

### Get places List [GET]

+ Parameters

    + people (required, integer, `2`) ... Số lượng người
    + sortBy (required, string, `time`)
        + `time`
        + `price`
        + `localtion`
        + `favorite`
    + priceFrom (required, integer, `0`) 
    + priceTo (required, integer, `150000`)
    + rating (required, integer, `4`)
    + cuisine (required, integer, `1`)
    + hasDiscount (optional, integer, `1`)
    + lat (required, float, `10.747426`) ... Latitude của location hiện tại
    + long (required, float, `106.701245`) ... Longitude của location hiện tại
    + number = `20` (optional, integer, `25`) ... Số lượng nhà hàng muốn lấy


+ Response 200 (application/json)

        {
            "data": [
                {
                    "id": 11,
                    "name": "Ramiro",
                    "rating": 0,
                    "time_waiting": 900,
                    "latitude": "10.779011",
                    "longitude": "106.720009",
                    "discount": 5,
                    "distance": 4.07,
                    "categories" : {
                        "data" : [
                            {
                                "id" : 1,
                                "name" : Seafood
                            },
                            {
                                "id" : 2,
                                "name" : Beef
                            }
                        ]
                    }
                },
                {
                    "id": 80,
                    "name": "Elenora",
                    "rating": 0,
                    "time_waiting": 900,
                    "latitude": "10.710105",
                    "longitude": "106.715846",
                    "discount": 20,
                    "distance": 4.45,                    
                    "categories" : {
                        "data" : [
                            {
                                "id" : 1,
                                "name" : Seafood
                            },
                            {
                                "id" : 2,
                                "name" : Beef
                            }
                        ]
                    }
                },
            ]
        }

## places Detail [/places/{id}]
Manage an existing places.

+ Parameters

    + id (required, integer) ... The unique identifier of a place

### Get places Detail [GET]

+ Response 200 (application/json)

        {
            "data" : {
                "id": 2,
                "name": "Kielisski",
                "rating" : "4",
                "hours" : "9:00am - 11:00pm",
                "time_waiting" : "10",
                "image" : "1.jpg",
                "categories" : {
                    "data" : [
                        {
                            "id" : 1,
                            "name" : Seafood
                        },
                        {
                            "id" : 2,
                            "name" : Beef
                        }
                    ]
                },
                "description" : "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cum natus voluptates, velit quisquam, temporibus doloremque. Odio qui quis, magni, recusandae obcaecati debitis nobis ipsum aperiam. Tempora, quam molestias est vero?",
                "latitude": "10.710105",
                "longitude": "106.715846",
                "address" : "300 An Dương Vương Phường 10, Quận 5",
                "price" : "150.000 - 600.000",
                "payments" : {
                    "data" : [
                        {
                            "id" : 1,
                            "name" : "Cash"
                        },
                        {
                            "id" : 2,
                            "name" : "Paypal Payment"
                        },
                        {
                            "id" : 3,
                            "name" : "Online Payment"
                        }
                    ]
                },
                "parking" : {
                    "data" : [
                        {
                            "id" : 1,
                            "name" : "Street Parking"
                        },
                        {
                            "id" : 2,
                            "name" : "Parking Garage"
                        },
                        {
                            "id" : 3,
                            "name" : "Next Door"
                        }
                    ]
                },
                "menu_categories" : {
                    "data" : [
                        {
                            "id" : 1,
                            "name" : "Pizza",
                            "image" : "pizza.jpg"
                        },
                        {
                            "id" : 2,
                            "name" : "Burger",
                            "image" : "burger.jpg"
                        }
                    ]
                },
            }
        }

+ Response 404 (application/json)

        {
          "error" : {
            "http_code" : 404,
            "message" : "place Not Found"
          }
        }

## places Detail Reviews [/places/{id}/reviews]
+ Parameters

    + id (required, integer) ... The unique identifier of a place

### Get places Reviews [GET]

+ Response 200 (application/json)

        {
            "data" : [
                {
                    "user" : {
                        "data" : {
                            "id" : 1,
                            "fullname" : "Sarah Johnson",
                            "avatar" : "sarah-johnson.jpg"
                        }
                    },
                    "created_time" : "15:20",
                    "created_date" : "15.06.2016",
                    "content" : "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Minus ex beatae eos, facilis harum recusandae officiis tempora eum aut doloribus inventore nemo facere eaque quaerat cumque voluptatum tempore, eius qui.",
                    "images" : {
                        "data" : [
                            {
                                "id" : 1,
                                "image" : "1.jpg"
                            },
                            {
                                "id" : 2,
                                "image" : "2.jpg"
                            }
                        ]
                    }
                }
            ]
        }

+ Response 404 (application/json)

        {
          "error" : {
            "http_code" : 404,
            "message" : "place Not Found"
          }
        }

## places Detail Menu [/places/{id}/menu{?sortBy,categoryId}]
+ Parameters
    + id (required, integer) ... The unique identifier of a place
    + categoryId (required, integer, `1`)
    + sortBy (required, string, `delight`)
        + `delight`
        + `speed`
        + `price`

### Get places Menu [GET]


+ Response 200 (application/json)

        {
            "data" : [
                {
                    "id" : 1,
                    "name" : "Pizza",
                    "price" : "120.000 VND",
                    "description" : "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Odit minus ad animi soluta voluptas doloremque expedita, esse, laborum aliquid officia facere! Labore et odit cupiditate minima, distinctio nam fugit eum.",
                    "image" : "pizza.jpg",
                },
                {
                    "id" : 2,
                    "name" : "Burger",
                    "price" : "90.000 VND",
                    "image" : "burger.jpg",
                    "description" : "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Odit minus ad animi soluta voluptas doloremque expedita, esse, laborum aliquid officia facere! Labore et odit cupiditate minima, distinctio nam fugit eum.",
                }
            ]
        }

+ Response 404 (application/json)

        {
          "error" : {
            "http_code" : 404,
            "message" : "place Not Found"
          }
        }


# Group Checkins
Checkins and History.

## Check-in [/checkins]

### Create Check-in [POST]

+ Request (application/json)

      + Body

            {
                "place_id": 1,
                "people" : 2
            }

+ Response 201 (application/json)

        {
            "data": [
                "id": 1,
                "place_id": 1,
                "time": 10,
                "created_at": "2017-04-02 18:30:00",
                "status" : "waiting"
            ]
        }

## Cancel Checkin [/checkins/cancel]

### Cancel Check-in [POST]

+ Request (application/json)

      + Body

            {
                "place_id": 1,
                "people" : 2
            }

+ Response 201 (application/json)

        {
            "data": [
                "id": 1,
                "place_id": 1,
                "time": 10,
                "created_at": "2017-04-02 18:30:00",
                "status" : "waiting"
            ]
        }

## Reservation [/reservations]

### Create Reservation [POST]

+ Request (application/json)

      + Body

            {
                "place_id": 1,
                "people" : 2,
                "date" : "Jan 2, 2016",
                "hours" : "7:00 AM",
                "note" : "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptates itaque excepturi sit, corrupti quasi quam temporibus eaque perferendis accusamus quisquam adipisci soluta culpa et alias labore, facere in qui nobis."
            }

+ Response 201 (application/json)

        {
            "data": [
                "id": 1,
                "date": "7:00 PM Jan 2, 2017",
                "people": 2,
                "status" : "success",
                "code" : "T83F3"
            ]
        }

## Histories [/histories]

### Get Histories [GET]

+ Response 200 (application/json)

        {
            "data": [
                {
                    "id": 2,
                    "place" : {
                        "data" : [
                            "name": "Kielisski",
                            "address" : "Nguyễn Trãi",
                        ],
                    },
                    "date" : "7:00 Jan 2, 2017",
                    "cost" : "3.000.000 VND",
                    "code" : "U93DG3",
                    "people" : 2,
                    "status" "waiting"
                },
                {
                    "id": 1,
                    "place" : {
                        "data" : [
                            "name": "Kielisski",
                            "address" : "Nguyễn Trãi",
                        ],
                    },
                    "date" : "7:00 Jan 2, 2017",
                    "cost" : "3.000.000 VND",
                    "code" : "U93DG3",
                    "people" : 2,
                    "status" "complete"
                }
            ]
        }

