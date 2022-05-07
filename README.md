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
Read on [http made really easy](https://www.jmarshall.com/easy/http/) to understand what is the protocol HTTP. This is the main protocol on which the internet websites is built.

### NodeJS
[NodeJS](https://nodejs.org/en/) is a javascript runtime commonly used to build backends in javascript

### Express
[Express](https://expressjs.com/) is a simple framework in NodeJS used to make javascript backends run on NodeJS.

## Super Hero Project
The Super Hero is a RESTful API to manage super heroes and their missions. 

You can read/create/update/delete heroes and missions.

One hero can have many mission (one-to-many relationship). 

Each hero and mission has a unique ID. 

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
### GET /api/v1/superheroes
Returns a list of all the super heroes

### POST /api/v1/superheroes
Create a new hero

### PUT /api/v1/superheroes/{id}
Update hero {id}

### DELETE /api/v1/superheroes/{id}
Delete hero {id}

### GET /api/v1/missions
Returns a list of all the missions

### POST /api/v1/missions
Create a new mission

### PUT /api/v1/missions/{id}
Update mission {id}

### DELETE /api/v1/missions/{id}
Delete mission {id}

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

The API must implement all the functionalities describe in the Super Hero Project.

