## Exercise 1: First Component

1. In `ReactDemos` folder
1. Write a `Greeter` component in React that returns an `h2` with "Hello" inside of the element.
1. Call it using this code ReactDOM.createRoot(document.getElementById("root")).render(<Greeter />);
   1.Run `npm start` to see the result on the index.html page.

## Exercise 2: Props

1. In `ReactDemos` folder
1. Update the `Greeter` component in React to return an `h2` with "Hello Calvin Broadus" inside of the element. The name should come through props.
1. Call it using this code
   `   ReactDOM.createRoot(document.getElementById("root")).render(<Greeter first="Calvin" last="Broadus" />);`
   1.Refresh index.html page to see the result.
1. Then change the name of the props coming in to another name. Verify it works.
1. Add an age prop and display it.
1. If you aren't already use destructuring in the function parameters so that you don't have to say `props.first` etc...

   ```js
   function Greeter({ first, last, age }) {
     //we are doing this above in the function components parameter list ()
     // let { first, last, age } = props;

     return (
       <h2>
         Hello {first} {last}. He is {age} years old.
       </h2>
     );
   }

   ReactDOM.createRoot(document.getElementById("root")).render(
     <Greeter first="Calvin" last="Broadus" age="52" />
   );
   ```

1. Bonus: Pass the props from an object into the HTML tag for the component

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

   let person = {
     first: "Calvin",
     last: "Broadus",
     age: 52,
   };

   ReactDOM.createRoot(document.getElementById("root")).render(
     <Greeter first={person.first} last={person.last} age={person.age} />
   );
   ```

## Exercise 3: Event Handling

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
           necessitatibus minima accusamus. Quidem perferendis eligendi ipsum
           eum repellat, nihil totam, vero, similique suscipit quibusdam
           architecto. Esse dolores voluptates odit laborum.
         </p>
         <button onClick={display}>Display</button>
       </div>
     );
   }

   ReactDOM.createRoot(document.getElementById("root")).render(<App />);
   ```

### Exercise 4: State

1. Create a component `App` and render it
1. Inside the component, put a `message` variable in state and initialize to an empty string "".
1. Add a `button` with the text **Display**
1. Add a `display` function that sets the button to "Message in the bottle"
1. Associate the `display` function with the `onClick` event of the button
1. Open the page, click the `button` and verify the message appears.

   ```js
   //component function
   function App() {
     //code
     // let message = "";
     const [message, setMessage] = React.useState("");

     function display() {
       // message = "Message in the bottle";
       setMessage("Message in the bottle");
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

## Exercise 6: Conditional Rendering

1. Create an `App` component and render it inside the root element
1. In the `App` component
   - create a state variable for the currently signed in user called `user`
     - initialize it to `undefined`
     - make a copy of the state variable line and in the duplicated line initialize user state to the following user object
       ```
       {
         first: "James"
         last: "Roday"
       }
       ```
     - comment out the last line where you set the user to an object (for now)
1. Create an `AccountHeader` component
   - render it inside the `App` component
   - pass the `user` state variable as a prop into `AccountHeader`
1. In the `AccountHeader`
   - add a Sign In link (anchor element)
   - add a span element with nothing inside it for now (it will hold the signed in user's name)
   - use the conditional (ternary) operator to check if the user prop exists
     - if `user` display user's first and last name properties inside the
     - else display Sign In link
1. Open the page and verify the link is shown
1. Comment out the line setting user state to `undefined` and uncomment the line setting it to a `user` object

   - Reload and verify the user's first and last name is shown

<!-- ## Exercise 6B: More Conditional Rendering

1. Create a dropdown menu composed of a button and an unordered list of menu items
1. When you click the button hide or show the menu
1. Achieve this using all 3 different syntaxes:
   - if
   - ?
   - && -->

## Exercise 7: Child to Parent Communication

1. Start with the following code

   ```js
   const { useState } = React;

   function FruitListItem(props) {
     return (
       <li>
         {props.fruit.name} | <button>Delete</button>
       </li>
     );
   }

   function FruitList() {
     const [fruits, setFruits] = useState([
       { id: 1, name: "apple" },
       { id: 2, name: "orange" },
       { id: 3, name: "blueberry" },
       { id: 4, name: "banana" },
       { id: 5, name: "kiwi" },
     ]);

     return (
       <ul>
         {fruits.map((fruit) => (
           <FruitListItem key={fruit.id} fruit={fruit} />
         ))}
       </ul>
     );
   }

   function App() {
     return <FruitList />;
   }

   ReactDOM.createRoot(document.getElementById("root")).render(<App />);
   ```

1. Add the function `removeFruit` inside the `FruitList` component
   - the function should take a `fruit `as a parameter
   - use the Array `filter` method to filter out the `fruit` that should be removed and return a new array into a variable you create named `updatedFruits`
   - use the state setter function `setFruits` to update the `fruits` state with the `updatedFruits` array
1. Pass the `removeFruit` function as a prop into each `FruitListItem`. Name the prop `onRemove`
1. Associate the click event of the button in `FruitListItem` with the function coming into props named `onRemove`
   - you need to pass the prop fruit for a given `FruitListItem` to the onRemove function so you will need to wrap `onRemove` in an arrow function to delay the calling of the function until the button is clicked
1. Test the app and verify the appropriate `fruit` is removed when the **delete** button is clicked

---

### Exercise 8: useEffect

1. **Set Up the HTML and CSS:**

   - Update your `index.html` file to include a link to a `styles.css` stylesheet inside the `<head>` tag as follows:
     ```html
     <link rel="stylesheet" href="styles.css" />
     ```
   - Add the following CSS to your `styles.css` file:
     ```css
     .card {
       border: 1px solid lightgray;
       padding: 2rem;
       width: 18rem;
     }
     ```

2. **Create the React Component:**

   - Create a component named `App` and render it inside the root element.
   - Inside the `App` component:
     - Initialize a state variable called `busy` to `false`.
     - Initialize another state variable called `teams` to an empty array.
   - Create a function named `loadTeams` that does the following:
     - Sets `busy` to `true`.
     - After a delay of 1 second, sets `busy` back to `false` and updates the `teams` state with an array of NBA teams (you can use the provided `nbaTeams` array).

3. **Use useEffect to Load Data:**

   - Use the `useEffect` hook to call `loadTeams` when the component mounts.

4. **Render the Teams with Styling:**

   - Inside the `App` component's JSX:
     - Conditionally render a paragraph element with "Loading..." text when `busy` is `true`.
     - Map over the `teams` array to display each team’s name and division inside a `div` element with a `className` of `"card"`.

5. **Run the Application:**

   - Test the application to ensure that the "Loading..." text appears briefly before the list of NBA teams is displayed, with the `.card` styling applied to each team.

   <!-- #### `main.js`

   ```js
   const { useState, useEffect } = React;

   const nbaTeams = [
     { name: "Los Angeles Lakers", division: "Pacific" },
     { name: "Chicago Bulls", division: "Central" },
     { name: "Miami Heat", division: "Southeast" },
     { name: "Dallas Mavericks", division: "Southwest" },
   ];

   function App() {
     const [busy, setBusy] = useState(false);
     const [teams, setTeams] = useState([]);
     function loadTeams() {
       setBusy(true);
       setTimeout(() => {
         setBusy(false);
         setTeams(nbaTeams);
       }, 1000);
     }

     useEffect(loadTeams, []);

     return (
       <div>
         {busy && <p>Loading...</p>}
         {teams.map((team) => (
           <div className="card" key={team.name}>
             <strong>{team.name}</strong>
             <div>{team.division}</div>
           </div>
         ))}
       </div>
     );
   }

   ReactDOM.createRoot(document.getElementById("root")).render(<App />);
   ```

   #### `styles.css`

   ```css
   .card {
     border: 1px solid lightgray;
     padding: 2rem;
     width: 18rem;
   }
   ``` -->



## Exercise 9: Forms | Controlled Components

sign in

## Exercise 10: Forms | Validation

sign in

## Exercise 11: Forms | Data with React Hook Form

sign in

## Exercise 12: Forms | Validation with React Hook Form

sign in

## Exercise 13: Promises and async await

## Exercise 14: fetch API

## Exercise 15: Router
```
