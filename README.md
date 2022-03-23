# Rick-and-Morty-Website

### General Assembly Project 2

<img width="1423" alt="Screen Shot 2022-03-22 at 16 16 42" src="https://user-images.githubusercontent.com/91087641/159525827-4ce2dbac-e8ca-4cc8-9b59-320d92192c95.png">

## Brief 

Create a **React** application that consumes a public **API**, utilising the knowledge gained from the first five weeks of the SEI course. The React application must have several **components** and a **router** with **several "pages"**.

Paired project. 

Timeframe: 2 days.

## Deployment
Please follow this link to view the Project: https://rick-and-morty-sei61.netlify.app/

Repository link: https://github.com/PeterBid/rick-and-morty-website

## Team

#### • [Peter Bid (Me)](https://github.com/PeterBid) 

#### • [Thor Refoy](https://github.com/thor-r)

## Concept and API Used

We Built a React app within 48 hours. As fans of Rick and Morty we decided to build a fun, visually striking and interactive Rick and Morty application with audio in which you would be able to view characters from the televsion series. 

We then added the ability to filter characters by typing thier name and the click into character pages where the user could see more specific information about each character (Alive or Dead, Human or Alien, Male/Female/Unknown etc). 

The API we used can be found here [Rick and Morty API Documentation](https://rickandmortyapi.com/)  

## Instalation

Clone or download the repo.
Open it in editor of your choice and run `yarn` command in your terminal to install all dependencies.
Start server with `yarn start`.

## Technologies Used

* React
* JSX
* Axios
* SCSS
* CSS
* JavaScript
* HTML5
* Yarn
* VS Code
* VS Code LiveShare
* Insomnia
* Git and GitHub 
* Canva (for gifs and images)
* Netlify (deployment)
   

## Process

### Planning

As this project's deadline was less than 48 hours after being given the brief, we had to quickly plan together. 

We decided we should pick an API that we enjoyed the content of, but also one with enough data, images and good documentation to give ourselves the best advantage. After browsing through many public APIs, we found `The Rick and Morty API`, an ideal API that met our criteria.

Afterwards we tested the API's responses and reaching specific endpoints by using `Insomnia` to ensure we were getting what we needed. This allowed us to plan out what information we wished to target upon each request to reach out minimun viable product.

Upon targeting each endpoint we then mapped out how we wished the site to look. We decided to keep our application simple with just a few "pages" so we could focus on it on reaching the minimum viable product and have something looking well polished with the features are working as intended in the timeframe.

We also decided to use VSCode Liveshare for this project so we can collaboratively work on the same code base together. It helped us considerably as we could easily spot whether anything was missing in our code, and we could debug our code faster by doing it together. We also effectively consolidated our knowledge together with this approach.

#### Wire Frame

![rick morty plan](https://user-images.githubusercontent.com/91087641/159555224-de12f8ea-c51e-444f-8bd9-7cb379b2f192.png)


#### Testing With Insomnia

<img width="536" alt="Screen Shot 2022-01-26 at 15 28 32" src="https://user-images.githubusercontent.com/91087641/159555394-e01299a3-a4b5-47db-b878-6506d7279022.png">

<img width="603" alt="Screen Shot 2022-01-26 at 15 22 02" src="https://user-images.githubusercontent.com/91087641/159555458-7ddc2969-09a1-4173-b5c4-9b2f78cc5ebc.png">

### Creating the Front End with React

#### Styling and Audio

This was the first project in which I worked with the `SCSS`. `SCSS` made styling the `CSS` and positioning `HTML` elements much easier and smoother as we could use a wide range of colours and styles for classes quickly and effectively across the site. 

We wished to create an application which reflected the Rick and Morty universe. We achieved this by having the colour scheme and styling of our website strongly imitate that of the television series. In order to emphasize this even further and make our website even more interactive, we added various images and gifs customly made using `Canva`. 

We also added different sound effects from the show, the choice of these were tailored specific functions to enchance the user experiance. For example choosing Morty saying "What's you name?" when the user clicks to search a character by name.
