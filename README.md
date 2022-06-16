# Code Snippets

# ----------------------------------- 
open the project in your IDE 
and open up the pubspec.yaml file 
and add up the following dependencies that 
we require,

dependencies:

    freezed_annotation: ^2.0.3
    dio: ^4.0.6
dev_dependencies:

    build_runner: ^2.1.11
    freezed: ^2.0.3+1
    json_serializable:

JSONPlaceholder response
```json
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
      "street": "Kulas Light",
      "suite": "Apt. 556",
      "city": "Gwenborough",
      "zipcode": "92998-3874",
      "geo": {
        "lat": "-37.3159",
        "lng": "81.1496"
      }
    },
    "phone": "1-770-736-8031 x56442",
    "website": "hildegard.org",
    "company": {
      "name": "Romaguera-Crona",
      "catchPhrase": "Multi-layered client-server neural-net",
      "bs": "harness real-time e-markets"
    }
  }
]
```
When taking a closer look at it we can identify the following,

    "id" is of type int because it returns a single digit
    
    "name" contains various characters, so this is a String
    
    "username" is a String
    
    "email" is a String
    
    "address" is a JSON object, so we'll require to create its own data model as

well because we don't wanna put up a type for that as Map<String, dynamic>
that would make less robust
So let's identify the property types for each property in "address" field:

    "street" is a String
    
    "suite" is a String
    
    "city" is a String
    
    "zipcode" is a String

"geo" is another JSON object,
so we'll do the same thing as what we are currently doing for address
lat can be a String but since we know it is "latitude" and usually they are in decimal values,
so we'll use double for that instead

    lat is double
    
    lng is double

and other fields are :

    "phone" is a String
    
    "website" is a String
    
    "company" is a JSON object
    
    "name" is a String
    
    "catchPhrase" is a String
    
    "bs" is a String

##Creating a data model with freezed

## create a file as "freezed_datamodels"

