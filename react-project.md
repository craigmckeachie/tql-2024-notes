## Exercise 1

1.  Create an App component
1.  Create a MoviesPage component and render it inside the App component
1.  Create a state variable in the MoviesPage component and assign it to the provided array of movies
1.  Create a MovieList component and render it inside the MoviesPage component

- pass the movies from the page to the list component
- loop through the movies and display each movie name in a div
- style the movie data as a card
- the array of movie objects is at the bottom of this file

1. Verify the movies display

## Exercise 2

1. Create a MovieCard component

   - pass in the movie object
   - display the data just as you did in the list
     > TIP: You can remove the HTML/JSX to display the card from the list and put it in the MovieCard.

1. Verify the data still displays

## Exercise 3

1. Add an "Edit" button in each movie card
1. Write a function inside the component (it's an event handler) named `handleEdit`
   - `console.log` out the `movie` object passed into the card that was clicked
1. Associate the handleEdit function with the click of the button
1. Verify clicking the button displays the movie in the in the DevTools `console`

## Movies Data

This data is used in the above set of exercises.

```js
const movies = [
  {
    imdbID: "tt10872600",
    title: "Spider-Man: No Way Home",
    year: 2021,
    director: "Jon Watts",
    genre: "Action",
    rating: 8.4,
    budgetInMillions: 200,
  },
  {
    imdbID: "tt1160419",
    title: "Dune",
    year: 2021,
    director: "Denis Villeneuve",
    genre: "Sci-Fi",
    rating: 8.1,
    budgetInMillions: 165,
  },
  {
    imdbID: "tt1877830",
    title: "The Batman",
    year: 2022,
    director: "Matt Reeves",
    genre: "Action",
    rating: 8.3,
    budgetInMillions: 185,
  },
  {
    imdbID: "tt2382320",
    title: "No Time to Die",
    year: 2021,
    director: "Cary Joji Fukunaga",
    genre: "Action",
    rating: 7.3,
    budgetInMillions: 250,
  },
  {
    imdbID: "tt10838180",
    title: "The Matrix Resurrections",
    year: 2021,
    director: "Lana Wachowski",
    genre: "Sci-Fi",
    rating: 5.7,
    budgetInMillions: 190,
  },
  {
    imdbID: "tt9376612",
    title: "Shang-Chi and the Legend of the Ten Rings",
    year: 2021,
    director: "Destin Daniel Cretton",
    genre: "Action",
    rating: 7.4,
    budgetInMillions: 150,
  },
  {
    imdbID: "tt2953050",
    title: "Encanto",
    year: 2021,
    director: "Byron Howard, Jared Bush",
    genre: "Animation",
    rating: 7.9,
    budgetInMillions: 120,
  },
  {
    imdbID: "tt8847712",
    title: "The French Dispatch",
    year: 2021,
    director: "Wes Anderson",
    genre: "Comedy",
    rating: 7.2,
    budgetInMillions: 25,
  },
  {
    imdbID: "tt11286314",
    title: "Don't Look Up",
    year: 2021,
    director: "Adam McKay",
    genre: "Comedy",
    rating: 7.2,
    budgetInMillions: 75,
  },
  {
    imdbID: "tt6334354",
    title: "The Suicide Squad",
    year: 2021,
    director: "James Gunn",
    genre: "Action",
    rating: 7.2,
    budgetInMillions: 185,
  },
  {
    imdbID: "tt6264654",
    title: "Free Guy",
    year: 2021,
    director: "Shawn Levy",
    genre: "Comedy",
    rating: 7.1,
    budgetInMillions: 100,
  },
  {
    imdbID: "tt3228774",
    title: "Cruella",
    year: 2021,
    director: "Craig Gillespie",
    genre: "Comedy",
    rating: 7.4,
    budgetInMillions: 100,
  },
  {
    imdbID: "tt9032400",
    title: "Eternals",
    year: 2021,
    director: "Chloé Zhao",
    genre: "Action",
    rating: 6.4,
    budgetInMillions: 200,
  },
  {
    imdbID: "tt8332922",
    title: "A Quiet Place Part II",
    year: 2021,
    director: "John Krasinski",
    genre: "Horror",
    rating: 7.3,
    budgetInMillions: 61,
  },
  {
    imdbID: "tt3480822",
    title: "Black Widow",
    year: 2021,
    director: "Cate Shortland",
    genre: "Action",
    rating: 6.7,
    budgetInMillions: 200,
  },
  {
    imdbID: "tt0870154",
    title: "Jungle Cruise",
    year: 2021,
    director: "Jaume Collet-Serra",
    genre: "Adventure",
    rating: 6.6,
    budgetInMillions: 200,
  },
  {
    imdbID: "tt4513678",
    title: "Ghostbusters: Afterlife",
    year: 2021,
    director: "Jason Reitman",
    genre: "Comedy",
    rating: 7.1,
    budgetInMillions: 75,
  },
  {
    imdbID: "tt12801262",
    title: "Luca",
    year: 2021,
    director: "Enrico Casarosa",
    genre: "Animation",
    rating: 7.5,
    budgetInMillions: 50,
  },
  {
    imdbID: "tt1321510",
    title: "In the Heights",
    year: 2021,
    director: "Jon M. Chu",
    genre: "Drama",
    rating: 7.3,
    budgetInMillions: 55,
  },
  {
    imdbID: "tt11214590",
    title: "House of Gucci",
    year: 2021,
    director: "Ridley Scott",
    genre: "Drama",
    rating: 6.6,
    budgetInMillions: 75,
  },
];
```
