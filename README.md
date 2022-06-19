# Consuming the REST API with Freezed

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

# main file :
create a function  in main file and called "fetchUsers" that 
will fetch data from this 

endpoint:
[https://jsonplaceholder.typicode.com/users](https://jsonplaceholder.typicode.com/users) to get user data 

and complete widgets like main.dart 

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

## create a file with name of "model1"

## fill file like "model1" class and then call build_runner

```bash
 flutter pub run build_runner build --delete-conflicting-outputs
```
To break it down what each does, the flutter pub run will allow us to run 
script coming from a package like build_runner 
and the build is the command or script to tell the 
build_runner package to start generating code for us.
It will look for files that contains the following *.freezed.dart 
and *.g.dart the * is just a wild card that means any file name 
that contains it will be recognized by the build_runner and
lastly the --delete-conflicting-outputs flag will tell 
the build_runner package to delete any existing *.freezed.dart
and *.g.dart files to prevent duplicate outputs or that 
it could potentially conflict with those.

So every time you might have to update your data model 
with new properties, you will always have to execute this 
the command snippet above to tell build_runner to generate code for us.


# the result of project :
    
<img src="https://res.cloudinary.com/practicaldev/image/fetch/s--vgCw5i3u--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8mvv1n5a5q33mevmwswo.png" alt="J"/>

# Using "copyWith" method from a data model

```dart
void appendUsername(int index) {
    setState(() {
      _users[index] = _users[index].copyWith(
        username: '${_users[index].username} CLICKED',
      );
    });
  }

// ... 

body: ListView.builder(
        itemCount: _users.length,
        itemBuilder: (context, index) {
          final user = _users[index];

          return ListTile(
            title: Text(user.username),
            subtitle: Text(user.email),
            onTap: () => appendUsername(index),
          );
        },
      ),
```