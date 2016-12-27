FORMAT: 1A
HOST: http://mogo.com/api

# Mogo API

## Authorization
Updating

# Group Restaurants
Search and manage restaurants.

## Restaurants List [/restaurants{?people,sortBy,priceFrom,priceTo,rating,cuisine,number,hasDiscount}]

### Get Restaurants List [GET]

+ Parameters

    + people (required, integer, `2`) ... Số lượng người
    + sortBy (required, string, `time`)
        + `time`
        + `price`
        + `localtion`
        + `favorite`
    + priceFrom (required, integer, `0`) 
    + priceTo (required, integer, `1000`)
    + rating (required, integer, `4`)
    + cuisine (required, integer, `1`)
    + hasDiscount (optional, integer, `1`)
    + number = `20` (optional, integer, `25`) ... Số lượng nhà hàng muốn lấy


+ Response 200 (application/json)

        {
            "data": [
                {
                    "id": 2,
                    "name": "Kielisski",
                    "rating" : "4",
                    "time_waiting" : "10",
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
                    "id": 1,
                    "name": "Hokkaido Shushi",
                    "rating" : "5",
                    "time_waiting" : "30",
                    "categories" : {
                        "data" : [
                            {
                                "id" : 3,
                                "name" : "Buffet"
                            }
                        ]
                    }
                },
            ]
        }

## Restaurants Map [/restaurants/map{?people,lat,long,distance}]

### Get Restaurants Map [GET]

+ Parameters

    + people (required, integer, `2`) ... Số lượng người
    + lat (required, float, `40.7641`) ... Latitude của location hiện tại
    + long (required, float, `-73.9866`) ... Longitude của location hiện tại
    + distance (required, integer, `20`) ... độ lớn radius muốn quét


+ Response 200 (application/json)

        {
            "data": [
                {
                    "id": 2,
                    "name": "Kielisski",
                    "rating" : "4",
                    "time_waiting" : "10",
                    "lat" : "40.7641",
                    "long" : "-73.9866",
                },
                {
                    "id": 1,
                    "name": "Hokkaido Shushi",
                    "rating" : "5",
                    "time_waiting" : "30",
                    "lat" : "40.7641",
                    "long" : "-73.9866",
                },
            ]
        }

## Restaurants Detail [/restaurants/{id}]
Manage an existing restaurants.

+ Parameters

    + id (required, integer) ... The unique identifier of a restaurant

### Get Restaurants Detail [GET]

+ Response 200 (application/json)

        {
            "data" : {
                "id": 2,
                "name": "Kielisski",
                "rating" : "4",
                "hours" : "9:00am - 11:00pm",
                "time_waiting" : "10",
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
                "lat" : "40.7641",
                "long" : "-73.9866",
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
                            "image_path" : "pizza.jpg"
                        },
                        {
                            "id" : 2,
                            "name" : "Burger",
                            "image_path" : "burger.jpg"
                        }
                    ]
                },
                "menu" : {
                    "data" : [
                        {
                            "id" : 1,
                            "name" : "Pizza",
                            "price" : "120.000 VND",
                            "description" : "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Odit minus ad animi soluta voluptas doloremque expedita, esse, laborum aliquid officia facere! Labore et odit cupiditate minima, distinctio nam fugit eum.",
                            "image_path" : "pizza.jpg",
                            "speed" : "5",
                            "delight" : "5",
                            "category_id" : 1
                        },
                        {
                            "id" : 2,
                            "name" : "Burger",
                            "price" : "90.000 VND",
                            "image_path" : "burger.jpg",
                            "description" : "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Odit minus ad animi soluta voluptas doloremque expedita, esse, laborum aliquid officia facere! Labore et odit cupiditate minima, distinctio nam fugit eum.",
                            "speed" : "4",
                            "delight" : "4",
                            "category_id" : 2
                        }
                    ]
                },
            }
        }

+ Response 404 (application/json)

        {
          "error" : {
            "http_code" : 404,
            "message" : "Restaurant Not Found"
          }
        }

## Restaurants Detail Reviews [/restaurants/{id}/reviews]
+ Parameters

    + id (required, integer) ... The unique identifier of a restaurant

### Get Restaurants Reviews [GET]

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
                                "image_src" : "1.jpg"
                            },
                            {
                                "id" : 2,
                                "image_src" : "2.jpg"
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
            "message" : "Restaurant Not Found"
          }
        }

# Group Checkins
Search and manage checkins.

## Check-in [/checkins]

### Create Check-in [POST]

+ Request (application/json)

      + Body

            {
                "restaurant_id": 1,
                "people" : 2
            }

+ Response 201 (application/json)

        {
            "data": [
                "id": 1,
                "restaurant_id": 1,
                "time": 10,
                "created_at": "2017-04-02 18:30:00",
                "status" : "waiting"
            ]
        }

## Reservation [/reservation]

### Create Reservation [POST]

+ Request (application/json)

      + Body

            {
                "restaurant_id": 1,
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
                    "restaurant" : {
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
                    "restaurant" : {
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

