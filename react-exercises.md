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
1. Comment out the line setting user state to undefined and uncomment the line setting it to a user object

   - Reload and verify the user's first and last name is shown

## Exercise 6B: More Conditional Rendering

1. Create a dropdown menu composed of a button and an unordered list of menu items
1. When you click the button hide or show the menu
1. Achieve this using all 3 different syntaxes:
   - if
   - ?
   - &&
