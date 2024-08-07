## Exercise 1

1. In `ReactDemos` folder
1. Write a `Greeter` component in React that returns an `h2` with "Hello" inside of the element.
1. Call it using this code ReactDOM.createRoot(document.getElementById("root")).render(<Greeter />);
   1.Run `npm start` to see the result on the index.html page.

## Exercise 2

1. In `ReactDemos` folder
1. Update the `Greeter` component in React to return an `h2` with "Hello Calvin Broadus" inside of the element. The name should come through props.
1. Call it using this code
   `   ReactDOM.createRoot(document.getElementById("root")).render(<Greeter first="Calvin" last="Broadus" />);`
   1.Refresh index.html page to see the result.
1. Then change the name of the props coming in to another name. Verify it works.
1. Add an age prop and display it.
1. If you aren't already use destructuring in the function parameters so that you don't have to say `props.first` etc...

1. Pass the props from an object into the HTML tag for the component

```js
function Greeter({ first, last, age }) {
  // let { first, last, age } = props;
  // console.log(JSON.stringify(props, null, ""));

  return (
    <h2>
      Hello {first} {last}. He is {age} years old.
    </h2>
  );
}

ReactDOM.createRoot(document.getElementById("root")).render(
  <Greeter first="Kanye" last="West" age="47" />
);
```

## Exercise 3

1. Create an `App` component and have React render it instead of `Greeter`
2. In the `App` component start with a div with a paragraph of "lorem ipsum" inside of it.
3. Test and verify that works.
4. Add an HTML `button` element below the paragraph and have the button text say "Display"
5. Create a function named display which calls the function `alert("Boo")`
6. Associate the function to the click event of the button
7. Verify it works.

```js
//component function
function App() {
  //code
  function display() {
    alert("Boo");
  }

  //html
  return (
    <div>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Laudantium
        necessitatibus minima accusamus. Quidem perferendis eligendi ipsum eum
        repellat, nihil totam, vero, similique suscipit quibusdam architecto.
        Esse dolores voluptates odit laborum.
      </p>
      <button onClick={display}>Display</button>
    </div>
  );
}

ReactDOM.createRoot(document.getElementById("root")).render(<App />);
```

### State Example

```js
//component function
function App() {
  // let message = "";
  const [message, setMessage] = React.useState("");
  //code
  function display() {
    // message = "Hey yo!";
    setMessage("Hey yo!");
  }

  //html
  return (
    <div>
      <button onClick={display}>Display</button>
      <p> {message} </p>
    </div>
  );
}

ReactDOM.createRoot(document.getElementById("root")).render(<App />);
```

```js
//component function
function App() {
  // let message = "";
  const [message, setMessage] = React.useState("");

  //code
  function display() {
    // message = "Hey yo!";
    setMessage("Hey yo!");
  }

  function reset() {
    setMessage("");
  }

  //html
  return (
    <div>
      <button onMouseOver={display} onMouseOut={reset}>
        Display
      </button>
      <p> {message} </p>
    </div>
  );
}

ReactDOM.createRoot(document.getElementById("root")).render(<App />);
```

## Exercise 4

1. Add another `button` element to the page and have the button text say "Display Message"
1. Create a state variable named `message` using the `useState` hook and initialize the message to "" (empty string).
1. Create another paragraph on the page and have it display the message state variable
1. Create a function named `displayMessage` that sets the `message` state variable to "Message in the bottle"
1. Associate the click event of the "Display Message" button with the `displayMessage` function.
1. Verify it works.

## Exercise 5

1. Create a dropdown menu composed of a button and an unordered list of menu items
1. When you click the button hide or show the menu
1. Achieve this using all 3 different syntaxes:
   - if
   - ?
   - &&

## Exercise 6

1.  Create an App component
1.  Create a MoviesPage component and render it inside the App component
1.  Create a state variable in the MoviesPage component and assign it to the provided array of movies
1.  Create a MovieList component and render it inside the MoviesPage component
    - pass the movies from the page to the list component
    - loop through the movies and display each movie name in a div
    - style the movie data as a card
1. 
