# Learning how to code
Wanna become a developer ? Follow this guide


## Setup / Prepare environment
* Install WSL2 (ubuntu). In wsl, install
  * git
* IDE for frontend (vscode, other)
* Install [nvm](https://github.com/nvm-sh/nvm) in order to install NodeJS
* Install NodeJS version 16 using nvm

## Documentation / Learn more
### HTTP
Read on [http made really easy](https://www.jmarshall.com/easy/http/) to understand what is the protocol HTTP. This is the main protocol on which the internet is built.

### NodeJS
[NodeJS](https://nodejs.org/en/) is a javascript runtime commonly used to build backends in javascript

### Express
[Express](https://expressjs.com/) is a simple framework in NodeJS used to make javascript backends run on NodeJS.

### JSON
[JSON](https://www.json.org/json-en.html) (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate. We use this format to exchange data often through HTTP.

## Super Hero Project
The Super Hero is a RESTful API to manage super heroes and their missions. 

You can read/create/update/delete heroes and their missions.

One hero can have many missions (one-to-many relationship). 

Heroes and missions have a unique ID.

### Models
```
SuperHero {
  id int
  name string
  superpower string
  missions List[Mission]
}

Mission {
  id int
  name string
  superhero int ForeignKey superhero(id)
}
```

### Super Hero Backend
#### Endpoints
```
GET /api/v1/superheroes
Returns a list of all the super heroes

POST /api/v1/superheroes
Create a new hero

PUT /api/v1/superheroes/{id}
Update hero {id}

DELETE /api/v1/superheroes/{id}
Delete hero {id}

GET /api/v1/missions
Returns a list of all the missions

POST /api/v1/missions
Create a new mission

PUT /api/v1/missions/{id}
Update mission {id}

DELETE /api/v1/missions/{id}
Delete mission {id}
```

#### How to test your backend using [curl](https://curl.se/). Supposing your app runs on localhost port 3000
```
curl -X GET http://localhost:3000/api/v1/heroes
  Status code: 200
  Body: []

curl -X GET http://localhost:3000/api/v1/missions
  Status code: 200
  Body: []

curl -X POST -d '{"name": "superman", "superpower": "overpower"}' http://localhost:3000/api/v1/heroes
  Status code: 201
  Body: {
          "id": 1, 
          "name": "superman", 
          "superpower": "overpower", 
          "missions": []
        }

curl -X GET http://localhost:3000/api/v1/heroes
  Status code: 200
  Body: [
          { 
            "id": 1, 
            "name": "superman",  
            "superpower": "overpower", 
            "missions": []
          }
        ]

curl -X POST -d '{"name": "kill Lex Luthor", "superhero": 1}' http://localhost:3000/api/v1/missions
  Status code: 201
  Body: {
          "id": 1, 
          "name": "kill Lex Luthor", 
          "superhero": 1
        }

curl -X GET http://localhost:3000/api/v1/heroes
  Status code: 200
  Body: [
          { 
            "id": 1, 
            "name": "superman",  
            "superpower": "overpower", 
            "missions": [
              {
                "id": 1, 
                "name": "kill Lex Luthor", 
                "superhero": 1
              }
            ]
          }
        ]

curl -X GET http://localhost:3000/api/v1/missions
  Status code: 200
  Body: [
          {
            "id": 1, 
            "name": "kill Lex Luthor", 
            "superhero": 1
          }
        ]


curl -X PUT -d '{"name": "weakman", "description": "not so overpower now"}' http://localhost:3000/api/v1/heroes/1
  Status code: 200
  Body: {
          "id": 1, 
          "name": "weakman",  
          "superpower": "not so overpower now", 
          "missions": [
            {
              "id": 1, 
              "name": "kill Lex Luthor", 
              "superhero": 1
            }
          ]
        }

curl -X PUT -d '{"name": "Lex Luthor is not killable"}' http://localhost:3000/api/v1/missions/1
  Status code: 200
  Body: {
          "id": 1, 
          "name": "Lex Luthor is not killable", 
          "superhero": 1
        }

curl -X DELETE http://localhost:3000/api/v1/heroes/1
  Status code: 400
  Body: {
          "error": "resource-is-binded", 
          "description": "Cannot delete resource hero(1) due to existing binding. Delete bindings before"
        }

curl -X DELETE http://localhost:3000/api/v1/missions/1
  Status code: 200

curl -X DELETE http://localhost:3000/api/v1/heroes/1
  Status code: 200

curl -X GET http://localhost:3000/api/v1/heroes
  Status code: 200
  Body: []

curl -X GET http://localhost:3000/api/v1/missions
  Status code: 200
  Body: []
```

## Homeworks
Here a list of homeworks with increasing difficulties. 

Create a github repository for each homework into your own github account.

Once you complete the assignment, commit and push into github in a feature branch. Then submit a pull request from your feature branch to your main branch for review.

### 1) Create a static website
You will build this web page in html, css, javascript. You do not have to use any framework. A simple index.html would suffice for this exercise. 

**Requirements**

The web page must have a title.

The webpage must have a font that you apply using css.

The web page must contain an image. The image must be of size 600 width, 400 height.

The web page must have a form which contains a counter field with a button increase and decrease the counter. The buttons must be styled with css. Check [here](https://drive.google.com/file/d/1nFJC_3jM0Yn7S64HhcI3Qrw3DghprrKa/view?usp=sharing) for a visual representation.

### 2) Create a simple backend in express/nodejs
You will build a simple backend API in [nodejs](https://nodejs.org/en/) using the framework [express](https://expressjs.com/). The backend must have all the feature describe in the Super Hero Project. Meaning you must be able to read/create/update/delete super heroes and their missions.

**Requirements**

The API must be RESTful.

The API consume and produce JSON. 

The API must implement all the functionalities describe in the Super Hero Project.

The API must pass tests describe in the [Super Hero Backend Test](#how-to-test-your-backend-using-curl-supposing-your-app-runs-on-localhost-port-3000) section

