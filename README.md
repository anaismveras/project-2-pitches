# Project 2 Pitch Guidelines
Project Description and Pitch Guidelines for SEIR SEA P2

---
## Project 2 Goals

In your second project you will create a full stack Express and Postgres app which has:
- *At least x2 models, and utilize and build at least one relationship between the two models.*
- *Sequelize as an ORM to interact with and create your database.*
- *An Express server utilizing EJS/EJS layouts for UI design and styling.*
- *Interaction with and inclusion of at least one API.*

## Project 2 Pitch Guidelines

In designing and building your project, you will start by forking and cloneing this repository, and then editing this README to include the following information: 
1. Name of your app
     - perfectPet 🐶

2. Tech stack you plan to use
     - Express, Ejs, Ejs-layouts, sequelize, method-override, axios

3. Simple wireframes
     * Can be handdrawn, or with tool of your choice
     * Example online tool: [Miro.com](https://miro.com/)
          - https://www.figma.com/file/ku8IuoGYtNKk7uuLVsqMvD/perfectPet?node-id=0%3A1
          
5. API you plan to use
     - https://www.petfinder.com/developers/v2/docs/

6. ERD
    - ![4320A604-A56C-4CC8-A808-647A05918A3A](https://user-images.githubusercontent.com/78924263/141371472-aaa80b2c-c8a4-455d-af4e-8a9315b10482.jpeg)

7. Example of how to call/invoke your API, and a description of what data comes back.
     - For Searched Animals by zipCode
          ``` js
          // For Searched Animals by zipCode
               app.get('/:location', (req, res) => {
               //will make the call after user puts in zipCode
               let animalsUrl = 'https://api.petfinder.com/v2/animals/${location}';

          axios.get(animalsUrl).then(apiRes => {
               let animals = apiRes.animals
          res.render('locationDetail', {animals});
               })
          }); 
          ```
     - To see information of Favorited Animal
          ```js
               router.get('/:id', (req, res)=> {
               let favePetInfo => req.params.id 
               let animalUrl = https://api.petfinder.com/v2/animals/${id}

          axios.get(animalUrl)
               .then(apiRes => {
                    let petImage = apiRes.animal.photos.medium
                    let petStatus = apiRes.animal.status
                    let petName = apiRes.animal.name
                    let petAge = apiRes.animal.age
                    let petBreed = apiRes.animal.breeds.primary
                    let petGender = apiRes.animal.gender
                    let petDescrption = apiRes.animal.description

          res.render('faveDetail', {petImage, petStatus, petName, petAge, petBreed, petGender, petDescrption})
          })
          .catch(error => {
          console.log(error)
               })
          }) 

          ```
     - Information comeback:
          - For Searched Animals by zipCode - all animals on petfinder API that is in that zip code with the disalibily === true
     ```js
          {
    "animals": [
        {
            "id": 124,
            "organization_id": "NJ333",
            "url": "https://www.petfinder.com/cat/nebula-124/nj/jersey-city/nj333-petfinder-test-account/?referrer_id=d7e3700b-2e07-11e9-b3f3-0800275f82b1",
            "type": "Cat",
            "species": "Cat",
            "breeds": {
                "primary": "American Shorthair",
                "secondary": null,
                "mixed": false,
                "unknown": false
            },
            "colors": {
                "primary": "Tortoiseshell",
                "secondary": null,
                "tertiary": null
            },
            "age": "Young",
            "gender": "Female",
            "size": "Medium",
            "coat": "Short",
            "name": "Nebula",
            "description": "Nebula is a shorthaired, shy cat. She is very affectionate once she warms up to you.",
            "photos": [
                {
                    "small": "https://photos.petfinder.com/photos/pets/124/1/?bust=1546042081&width=100",
                    "medium": "https://photos.petfinder.com/photos/pets/124/1/?bust=1546042081&width=300",
                    "large": "https://photos.petfinder.com/photos/pets/124/1/?bust=1546042081&width=600",
                    "full": "https://photos.petfinder.com/photos/pets/124/1/?bust=1546042081"
                }
            ],
            "videos": [
                {
                    "embed": "<iframe src=\"https://www.youtube.com/embed/xaXbs1fRFRM\" frameborder=\"0\" allowfullscreen></iframe>"
                }
            ],
            "status": "adoptable",
            "attributes": {
                "spayed_neutered": true,
                "house_trained": true,
                "declawed": false,
                "special_needs": false,
                "shots_current": true
            },
            "environment": {
                "children": false,
                "dogs": true,
                "cats": true
            },
            "tags": [
                "Cute",
                "Intelligent",
                "Playful",
                "Happy",
                "Affectionate"
            ],
            "contact": {
                "email": "petfindertechsupport@gmail.com",
                "phone": "555-555-5555",
                "address": {
                    "address1": null,
                    "address2": null,
                    "city": "Jersey City",
                    "state": "NJ",
                    "postcode": "07097",
                    "country": "US"
                }
            },
            "published_at": "2018-09-04T14:49:09+0000",
            "distance": 0.4095,
            "_links": {
                "self": {
                    "href": "/v2/animals/124"
                },
                "type": {
                    "href": "/v2/types/cat"
                },
                "organization": {
                    "href": "/v2/organizations/nj333"
                }
            }
        }
    ],
    "pagination": {
        "count_per_page": 20,
        "total_count": 320,
        "current_page": 1,
        "total_pages": 16,
        "_links": {}
    }
}

     ```
          - To see information of Favorited Animal - Animal's searched in API by id selected and pet's Image, Adoptablity status, Name, Age(young, adult, senoir), Breed, Gender and a Descrption 
     
     ``` 

          {
    "animal": {
            "id": 124,
            "organization_id": "NJ333",
            "url": "https://www.petfinder.com/cat/nebula-124/nj/jersey-city/nj333-petfinder-test-account/?referrer_id=d7e3700b-2e07-11e9-b3f3-0800275f82b1",
            "type": "Cat",
            "species": "Cat",
            "breeds": {
                "primary": "American Shorthair",
                "secondary": null,
                "mixed": false,
                "unknown": false
            },
            "colors": {
                "primary": "Tortoiseshell",
                "secondary": null,
                "tertiary": null
            },
            "age": "Young",
            "gender": "Female",
            "size": "Medium",
            "coat": "Short",
            "name": "Nebula",
            "description": "Nebula is a shorthaired, shy cat. She is very affectionate once she warms up to you.",
            "photos": [
                {
                    "small": "https://photos.petfinder.com/photos/pets/124/1/?bust=1546042081&width=100",
                    "medium": "https://photos.petfinder.com/photos/pets/124/1/?bust=1546042081&width=300",
                    "large": "https://photos.petfinder.com/photos/pets/124/1/?bust=1546042081&width=600",
                    "full": "https://photos.petfinder.com/photos/pets/124/1/?bust=1546042081"
                }
            ],
            "videos": [
                {
                    "embed": "<iframe src=\"https://www.youtube.com/embed/xaXbs1fRFRM\" frameborder=\"0\" allowfullscreen></iframe>"
                }
            ],
            "status": "adoptable",
            "attributes": {
                "spayed_neutered": true,
                "house_trained": true,
                "declawed": false,
                "special_needs": false,
                "shots_current": true
            },
            "environment": {
                "children": false,
                "dogs": true,
                "cats": true
            },
            "tags": [
                "Cute",
                "Intelligent",
                "Playful",
                "Happy",
                "Affectionate"
            ],
            "contact": {
                "email": "petfindertechsupport@gmail.com",
                "phone": "555-555-5555",
                "address": {
                    "address1": null,
                    "address2": null,
                    "city": "Jersey City",
                    "state": "NJ",
                    "postcode": "07097",
                    "country": "US"
                }
            },
            "published_at": "2018-09-04T14:49:09+0000",
            "distance": null,
            "_links": {
                "self": {
                    "href": "/v2/animals/124"
                },
                "type": {
                    "href": "/v2/types/cat"
                },
                "organization": {
                    "href": "/v2/organizations/nj333"
                }
            }
        }
}

     ```

8. MVP goals (x3-5)
     - Have users press a button to sign up/login and be put/aknowledged into a data base
     - Have users search by city name show pets in that area
     - Have users be able to press a button to favorite a pet to be added to a "favorite pets" list
     - Have users see their "favorite pets" list and be able to remove animals and see more about an animal by clicking the name
     - Use API call to show animal information

9. Stretch goals (x2-5)
     - Show ONLY animals with disabilities
     - Have User be able to go to the adoption agency website

10. Any potential roadblocks?
     - Not being able to ONLY show special needs pets since in the API it shows as a boolean
     - Not being able to get the API to get the write information for the pet
     - Not being able to get the CSS to look right

## How to get started
1. **Fork and clone this repository.**
2. **Edit the text above to include specifics of your project.**
3. **Commit, push, and submit a pull request to this repo with your edited pitch README.**
4. *After you have met with a staff member and your pitch has been approved, suggested next steps:*
      * Write out your routes and create a RESTful routing chart.
      * Come up with a breakdown of what you plan to accomplish each day and how you are going to accomplish it.
      * Create a new git repo for your project. 
      * Make all test API calls you need to to ensure your API will be usable for this project. 
      




