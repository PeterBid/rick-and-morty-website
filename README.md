# Rick-and-Morty-Website

### General Assembly Project 2

<img width="1423" alt="Screen Shot 2022-03-22 at 16 16 42" src="https://user-images.githubusercontent.com/91087641/159525827-4ce2dbac-e8ca-4cc8-9b59-320d92192c95.png">

## Table of Contents

- [Brief](#brief)
- [Deployment](#deployment)
- [Team](#team)
- [Concept](#concept-and-api-used)
- [Installation](#installation)
- [Technologies Used](#technologies-used)
- [Process](#process)
- [Planning](#planning)
- [Creating the Front End with React](#creating-the-front-end-with-react)
- [Challenges and Wins](#challenges-and-wins)
- [Future Improvements](#future-improvements)
- [Key Learnings](#key-learnings)
- [Contact](#contact)

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

We Built a React app within 48 hours. As fans of Rick and Morty we decided to build a fun, visually striking and interactive Rick and Morty application with audio in which you would be able to view characters from the television series. 

We then added the ability to filter characters by typing thier name and then click into character pages where the user could see more specific information about each character (Alive or Dead, Human or Alien, Male/Female/Unknown etc). 

The API we used can be found here [Rick and Morty API Documentation](https://rickandmortyapi.com/)  

## Installation

Clone or download the repo.
Open it in the editor of your choice and run `yarn` command in your terminal to install all dependencies.
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

As this project's deadline was less than 48 hours after being given the brief, we had to quickly make a plan together 

We decided we should pick an API that we enjoyed the content of, but also one with enough data, images and good documentation to give ourselves the best advantage. After browsing through many public APIs, we found `The Rick and Morty API`, an ideal API that met our criteria.

Afterwards we tested the API's responses and reached specific endpoints by using `Insomnia` to ensure we were getting what we needed. This allowed us to plan out what information we wished to target upon each request to reach our minimum viable product.

Upon targeting each endpoint we then mapped out how we wished the site to look. We decided to keep our application simple with just a few "pages" so we could focus on reaching the minimum viable product and have something looking well polished with the features that are working as intended in the timeframe.

We also decided to use VSCode Liveshare for this project so we can collaboratively work on the same code base together. It helped us considerably as we could easily spot whether anything was missing in our code, and we could debug our code faster by doing it together. We also effectively consolidated our knowledge together with this approach.

#### Wire Frame

![rick morty plan](https://user-images.githubusercontent.com/91087641/159555224-de12f8ea-c51e-444f-8bd9-7cb379b2f192.png)


#### Testing With Insomnia

<img width="536" alt="Screen Shot 2022-01-26 at 15 28 32" src="https://user-images.githubusercontent.com/91087641/159555394-e01299a3-a4b5-47db-b878-6506d7279022.png">

<img width="603" alt="Screen Shot 2022-01-26 at 15 22 02" src="https://user-images.githubusercontent.com/91087641/159555458-7ddc2969-09a1-4173-b5c4-9b2f78cc5ebc.png">

### Creating the Front End with React

#### Creating Components and Getting the Data form the API

* Character Index

For displaying the characters we created two components. The first component is `CharacterIndex`. After using a `get` axios request to receive the data we used the `map` method alongside `flexbox` to display the characters in a grid. 
```javascript
useEffect(() => {
    const getCharacters = async () => {
      try {
        const { data } = await axios.get('https://rickandmortyapi.com/api/character')
        setCharacters(data.results)

      } catch (err) {
        setIsError(true)
      }
    }
    getCharacters()
  }, [])
```
<img width="1395" alt="Screen Shot 2022-03-23 at 15 50 47" src="https://user-images.githubusercontent.com/91087641/159740885-4c3e4f9f-203e-4f58-93b9-d212a836f0b1.png">

* Filter Functionality

A `useState` of `searchTerm` alongside a text form targeting what users typed as a search term for character names was used to create a function to `filter` out results for the `map`. 

```javascript
 <div className='form_container'>
            <form onSubmit={handleSubmit}>
              <input type='text' id='charactersubmit' onClick={whatsYourNamePlay} placeholder="Submit a Character" onChange={event => {
                setSearchTerm(event.target.value)
              }} ></input>
            </form>
          </div>
          <ul className='characters_list'>
            <div className='characters_container'>{characters && characters.filter((character) => {
              if (searchTerm === '') {
                return character
              } else if (character.name.toLowerCase().includes(searchTerm.toLowerCase())) {
                return character 
              }
            }).map(character => {
              const { name, image, species, status, gender, id } = character
              return (
                <Link key={id} id="character_link" to={`/character/${character.id}`}>
                  <div className="character_card" >
                    <div className="character-name" >{name}</div>
                    <div className="character-status">Status: {status}</div>
                    <div className={character.image}><img src={image} /></div>
                  </div>
                </Link>
              )
            })}
            </div>
          </ul>
```
<img width="721" alt="Screen Shot 2022-03-23 at 15 51 02" src="https://user-images.githubusercontent.com/91087641/159740977-1a9faa98-597f-40eb-a824-4df71550c7c7.png">

* Character Show
 
We used the `id` of each character to create a `characterID` which then used with `useParams` created links to the `CharacterShow` component. If a user clicks on an individual character, they are redirected to a page with detailed information about that character. This was then used to return specific information related to each character.

```javascript
 const { characterId } = useParams()

  useEffect(() => {

    const getSingleCharacter = async () => {
      try {
        const { data } = await axios.get(`https://rickandmortyapi.com/api/character/${characterId}`)
        setCharacter(data)
        setLocation(data.location)
        setEpisode(data.episode)
        console.log(data)
      } catch (err) {
        console.log(err)
      }
    }
    getSingleCharacter()
  }, [characterId])
```
<img width="1426" alt="Screen Shot 2022-03-23 at 15 51 17" src="https://user-images.githubusercontent.com/91087641/159741125-38d93858-46bd-4947-9d8c-aa5c9450a297.png">

#### Styling and Audio

This was the first project in which I worked with the `SCSS`. `SCSS` made styling the `CSS` and positioning `HTML` elements much easier and smoother as we could use a wide range of colours and styles for classes quickly and effectively across the site. 

We wished to create an application which reflected the Rick and Morty universe. We achieved this by having the colour scheme and styling of our website strongly imitate that of the television series. In order to emphasise this even further and make our website even more interactive, we added various images and gifs customly made using `Canva`. 

We also added different sound effects from the show using the `useSound` package, the choice of these were tailored specific functions to enhance the user experience. For example choosing Morty saying "What's your name?" when the user clicks to search a character by name.

## Challenges and Wins

#### Challenges

Managing the short time in which to do the project. As this was only a 2 day project we had to work quickly, even with everything planned out. There were also additional features we wished to put in but had to be pragmatic to ensure we were focused on reaching the minimum viable product in the time frame.

Ensuring we had access to data endpoints deep down in the API for the character show page. Although it took longer than anticipated we learnt a lot about accessing and retrieving data from API's generally.

Responsive styling. As we built the site for desktop we ran out of time to implement responsive styling, therefore the components are not formatted correctly on mobile. In hindsight we would have planned for a mobile view from the start.
  
#### Wins

Planning. Having an effective and well thought out outline and plan of how to reach my minimum viable project really helped. This was especially emphasized with the time limit. It made the project, even when we had to rush, feel considerably less stressful. This was because we had clear objectives to aim towards, breaking the overall project down into much manageable bite-sized chunks.

Getting comfortable with adding unique gifs, importing images and gifs such as the spinner and using useSound package to add fun interactive aspects to overall user experience.

First pair coded project. I took great advantage of working with someone else sharing experience and different coding styles, while trying to collaboratively problem solve and taking advantage of VScode Liveshare. Thor and I were always in sync and found that bouncing personal ideas off each other always resulted in something better and it helped fixed errors considerably quicker too.

## Future Improvements

Make the project responsive to different screen sizes especially mobile.

Improving the filter functionality. This is so characters could be filtered on the basis of more conditions, not only on by name.

As well as a Characters API the Rick and Morty API Documentation also had a seperate Location and Episode API. Accessing these API's with Get requests and having separate index pages and show pages related to these API's as a way to expand the scale of the site. 


## Key Learnings

The project strongly cemented my knowledge of React. It transformed my understanding from the theoretical to the practical. This was across a wide range of areas, such as State, Hooks, Components and Routes. During this project React became one of my favourite frameworks to work with, especially in enjoying the sense of building that comes from it.

Using Axios. This project solidified my understanding of HTTP requests and using axios, for example reinforcing how asynchronous functions work and how promises are handled.

Planning. This project, especially with the quick deadline, helped me understand the importance of planning towards a minimum viable product effectively. Doing this helped us stay focused on what exactly was needed in the time frame and not get bogged down.

Pair Coding. I learned the importance of teamwork, and how to work productively as a pair.

Overall I was able to apply what I had learnt previously and much more doing this project.

It was a really big confidence boost in understanding React and made me excited to use React for future projects. I also really enjoyed pair coding, sharing ideas and solving problems together. Doing this project also made me look forward to coding in teams in the future.



## Contact

Social - www.linkedin.com/in/peter-bid

Email - peterbid21@gmail.com
