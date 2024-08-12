# React Exercises

- [React Exercises](#react-exercises)
  - [Exercise 1: First Component](#exercise-1-first-component)
  - [Exercise 2: Props](#exercise-2-props)
  - [Exercise 3: Event Handling](#exercise-3-event-handling)
  - [Exercise 4: State](#exercise-4-state)
  - [Exercise 5: Conditional Rendering](#exercise-5-conditional-rendering)
  - [Exercise 6: Child to Parent Communication](#exercise-6-child-to-parent-communication)
  - [Exercise 7: Async Data Fetching](#exercise-7-async-data-fetching)
  - [Exercise 8: Forms](#exercise-8-forms)
  - [Exercise 9: Form Validation](#exercise-9-form-validation)
  - [Exercise 10: Refactor Form with React Hook Form](#exercise-10-refactor-form-with-react-hook-form)
    - [Steps:](#steps)
  - [Exercise 11: Setting Up a REST API](#exercise-11-setting-up-a-rest-api)
  - [Exercise 12: GET from REST API](#exercise-12-get-from-rest-api)
  - [Exercise 13: Router](#exercise-13-router)
    - [Steps:](#steps-1)
    - [Tips:](#tips)
  - [Exercise 14: Route Parameters](#exercise-14-route-parameters)
  - [Exercise 15: More Forms Practice](#exercise-15-more-forms-practice)
  - [Exercise 16](#exercise-16)

## Exercise 1: First Component

1. In `ReactDemos` folder
1. Write a `Greeter` component in React that returns an `h2` with "Hello" inside of the element.
1. Render the component using this code:
   ```js
   ReactDOM.createRoot(document.getElementById("root")).render(<Greeter />);
   ```
1. Run `npm start` to see the result on the index.html page.

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

## Exercise 4: State

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

## Exercise 5: Conditional Rendering

1. Create an `App` component and render it inside the root element
1. In the `App` component
   - create a state variable for the currently signed in user called `user`
     - initialize it to `undefined`
     - make a copy of the state variable line and in the duplicated line initialize user state to the following user object
       ```
       {
         first: "James",
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

   #### `main.js`

   ```js
   const { useState } = React;

   function App() {
     const [user, setUser] = useState(undefined);
     // const [user, setUser] = useState({
     //   first: "James",
     //   last: "Roday",
     // });

     return (
       <>
         <AccountHeader user={user} />
       </>
     );
   }

   function AccountHeader(props) {
     return (
       <>
         {props.user ? (
           <span>
             Welcome, {props.user.first} {props.user.last}
           </span>
         ) : (
           <a href="#">Sign In</a>
         )}
       </>
     );
   }

   ReactDOM.createRoot(document.getElementById("root")).render(<App />);
   ```

<!-- ## Exercise 6B: More Conditional Rendering

1. Create a dropdown menu composed of a button and an unordered list of menu items
1. When you click the button hide or show the menu
1. Achieve this using all 3 different syntaxes:
   - if
   - ?
   - && -->

## Exercise 6: Child to Parent Communication

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

   #### `main.js`

   ```js
   const { useState } = React;

   function FruitListItem(props) {
     return (
       <li>
         {props.fruit.name} | <button onClick={props.onRemove}>Delete</button>
       </li>
     );
   }

   function FruitList() {
     //code

     //data
     const [fruits, setFruits] = useState([
       { id: 1, name: "apple" },
       { id: 2, name: "orange" },
       { id: 3, name: "blueberry" },
       { id: 4, name: "banana" },
       { id: 5, name: "kiwi" },
     ]);

     //functions/event handlers

     function removeFruit(fruit) {
       let updatedFruits = fruits.filter((f) => f.id !== fruit.id);
       setFruits(updatedFruits);
     }

     //html
     return (
       <ul>
         {fruits.map((fruit) => (
           <FruitListItem
             key={fruit.id}
             fruit={fruit}
             onRemove={() => removeFruit(fruit)}
           />
         ))}
       </ul>
     );
   }

   function App() {
     return <FruitList />;
   }

   ReactDOM.createRoot(document.getElementById("root")).render(<App />);
   ```

## Exercise 7: Async Data Fetching

This exercise demonstrates how to handle asynchronous data fetching and display the results.

1. **Starter Code:**

   - Use the following starter code to set up the fake API and define the `App` component:

   ```js
   const { useState, useEffect } = React;

   const nbaTeams = [
     { name: "Los Angeles Lakers", division: "Pacific" },
     { name: "Chicago Bulls", division: "Central" },
     { name: "Miami Heat", division: "Southeast" },
     { name: "Dallas Mavericks", division: "Southwest" },
   ];

   const teamAPI = {
     list() {
       return new Promise((resolve) => {
         setTimeout(() => {
           resolve(nbaTeams);
         }, 1000);
       });
     },
   };

   // Define the App component here
   function App() {
     // Your code will go here
   }

   ReactDOM.createRoot(document.getElementById("root")).render(<App />);
   ```

2. **Define the `App` Component:**

   - Inside `App`:
     - Use the `useState` hook to create two state variables:
       - `busy` to track whether data is being loaded (initialize it to `false`).
       - `teams` to store the list of teams (initialize it to an empty array).
     - Define an `async` function named `loadTeams` that:
       - Sets `busy` to `true`.
       - Uses `await` to get data from `teamAPI.list()`.
       - Sets `busy` to `false` after the data is loaded.
       - Updates the `teams` state with the retrieved data.
     - Use the `useEffect` hook to call `loadTeams` when the component mounts (an empty dependency array should be used).

3. **Render the Data:**

   - Inside the `App` component’s return statement:
     - Conditionally render a "Loading..." message if `busy` is `true`.
     - Add a div which will hold all the cards and give it a class of `list`
     - Map over the `teams` array and render each team in a `div` with the class name `card`. Each `div` should display the team’s name and division.

4. **Add Styles:**

- Create a `styles.css` file in your project directory.
- Define the `.card` class in `styles.css` with the following styles:

  ```css
  .list {
    display: flex;
    gap: 2rem;
    flex-wrap: wrap;
  }

  .card {
    border: 1px solid lightgray;
    padding: 2rem;
    width: 18rem;
  }
  ```

- Ensure that `styles.css` is linked in your `index.html` file:

  ```html
  <link rel="stylesheet" href="styles.css" />
  ```

  #### `main.js`

  ```js
  const { useState, useEffect } = React;

  const nbaTeams = [
    { name: "Los Angeles Lakers", division: "Pacific" },
    { name: "Chicago Bulls", division: "Central" },
    { name: "Miami Heat", division: "Southeast" },
    { name: "Dallas Mavericks", division: "Southwest" },
  ];

  const teamAPI = {
    list() {
      return new Promise((resolve) => {
        setTimeout(() => {
          resolve(nbaTeams);
        }, 1000);
      });
    },
  };

  function App() {
    const [busy, setBusy] = useState(false);
    const [teams, setTeams] = useState([]);
    async function loadTeams() {
      setBusy(true);
      let data = await teamAPI.list();
      setBusy(false);
      setTeams(data);
    }

    useEffect(function () {
      loadTeams();
    }, []);

    return (
      <div>
        {busy && <p>Loading...</p>}
        {teams?.map((team) => (
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

## Exercise 8: Forms

In this exercise, you'll build a Contact Us form with state management for multiple form fields and handle form submission.

1. **Set Up the Form Component:**

   - Create a component named `ContactUsForm` and render it inside the root element.
   - Inside the component:
     - Initialize three state variables: `department`, `message`, and `agreedToTerms`.
       - `department` is initialized to an empty string.
       - `message` is initialized to an empty string.
       - `agreedToTerms` is initialized to `false`.
     - Use `React.useState` to manage these state variables.

2. **Create the Form Layout:**

   - Create a `<form>` element and associate a `handleSubmit` function with the form’s `onSubmit` event handler.
   - Inside the form:
     - Add a `<select>` element for selecting a department with options for Human Resources, Public Relations, and Support. Register the `select` with the `department` state.
     - Add a `<textarea>` element for the message input, binding it to the `message` state.
     - Add a checkbox input with a label "I agree to the terms and conditions," and bind it to the `agreedToTerms` state.
     - Add a submit button labeled "Send."

3. **Handle Form Submission:**

   - Implement the `handleSubmit` function to prevent the default form submission behavior using `event.preventDefault()`.
   - Inside `handleSubmit`, log the form data to the console by converting the state to a string using the `stateToString` function.

4. **State to String Conversion:**

   - Implement a `stateToString` function to convert the form state into a JSON string for logging to the page.

5. **Testing the Form:**

   - Run the application and verify that the form behaves as expected:
     - When you select a department, enter a message, and check the "I agree to the terms and conditions" checkbox, the form state should update accordingly.
     - When you click "Send," the form data should be logged to the console as a JSON string by calling the `stateToString()` function.

   #### `main.js`

   ```js
   function ContactUsForm() {
     const [department, setDepartment] = React.useState("");
     const [message, setMessage] = React.useState("");
     const [agreedToTerms, setAgreedToTerms] = React.useState(false);

     function handleSubmit(event) {
       event.preventDefault();
       console.log("submitting", stateToString());
     }

     function stateToString() {
       return JSON.stringify(
         {
           department,
           message,
           agreedToTerms,
         },
         null,
         " "
       );
     }

     return (
       <form onSubmit={handleSubmit}>
         <select
           name="department"
           value={department}
           onChange={(e) => setDepartment(e.target.value)}
         >
           <option value="">Select...</option>
           <option value="hr">Human Resources</option>
           <option value="pr">Public Relations</option>
           <option value="support">Support</option>
         </select>
         <br />
         <br />
         <textarea
           name="message"
           value={message}
           onChange={(e) => setMessage(e.target.value)}
           cols="30"
           rows="10"
         />
         <br />
         <input
           type="checkbox"
           name="agreedToTerms"
           checked={agreedToTerms}
           onChange={(e) => setAgreedToTerms(e.target.checked)}
         />
         I agree to the terms and conditions.
         <br />
         <button>Send</button>
       </form>
     );
   }

   ReactDOM.createRoot(document.getElementById("root")).render(
     <ContactUsForm />
   );
   ```

## Exercise 9: Form Validation

In this exercise, you will create a contact form in React that includes validation and utilizes Bootstrap 5 for styling.

1. **Set Up the HTML File:**

   - Add the Bootstrap CSS file to your `index.html` by inserting the following line within the `<head>` tag:
     ```html
     <link
       href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
       rel="stylesheet"
     />
     ```
   - Ensure your custom `styles.css` file is linked **after** the Bootstrap CSS file:
     ```html
     <link rel="stylesheet" href="styles.css" />
     ```

2. **Define the App Component:**

   - Create a new React component named `App` that renders the `ContactUsForm` component inside a Bootstrap `div.container`.

3. **Set Up the Contact Form Component:**

   - Create a `ContactUsForm` component and include the following state variables using the `useState` hook:
     - you will need this statement `const { useState } = React;` at the top of the file so you just use `useState` instead of `React.useState`
     - `department` for the selected department.
     - `message` for the message text.
     - `agreedToTerms` for the checkbox indicating agreement to terms.
     - `errors` to track validation errors.

4. **Implement Form Validation:**

   - Write a `validateForm` function that checks if all fields are filled out:
     - The `department` field must not be empty.
     - The `message` field must not be empty.
     - The `agreedToTerms` checkbox must be checked.
   - If any field is invalid, store the corresponding error messages in the `errors` state.

5. **Handle Form Submission:**

   - Create a `handleSubmit` function that:
     - Prevents the default form submission behavior.
     - Calls `validateForm` to check for errors.
     - If validation passes, clears the `errors` state and logs the form data to the console.
     - If validation fails, updates the `errors` state with the appropriate messages.

6. **Render the Form with Bootstrap Classes:**

   - Style the form using Bootstrap classes:
     - Use `form-select` for the department dropdown, `form-control` for the message textarea, and `form-check-input` for the checkbox.
     - Add `is-invalid` classes dynamically based on whether each field has an error.
     - Display validation messages using `invalid-feedback` classes.

7. **Testing the Form:**
   - Verify that the form shows validation messages when fields are left empty.
   - Check that submitting the form with all fields completed logs the data to the console.

---

#### `index.html`

```html
<!DOCTYPE html>
<!-- index.html -->
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>React Demos</title>
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
      rel="stylesheet"
    />
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <div id="root"></div>

    <script src="/node_modules/react/umd/react.development.js"></script>
    <script src="/node_modules/react-dom/umd/react-dom.development.js"></script>
    <script src="/node_modules/@babel/standalone/babel.min.js"></script>
    <script type="text/babel" src="/main.js"></script>
  </body>
</html>
```

#### `main.js`

```js
const { useState } = React;

function ContactUsForm() {
  const [department, setDepartment] = useState("");
  const [message, setMessage] = useState("");
  const [agreedToTerms, setAgreedToTerms] = useState(false);
  const [errors, setErrors] = useState({});

  function validateForm() {
    const newErrors = {};
    if (!department) newErrors.department = "Department is required.";
    if (!message) newErrors.message = "Message is required.";
    if (!agreedToTerms)
      newErrors.agreedToTerms = "You must agree to the terms.";
    return newErrors;
  }

  function handleSubmit(event) {
    event.preventDefault();
    const validationErrors = validateForm();
    if (Object.keys(validationErrors).length > 0) {
      setErrors(validationErrors);
    } else {
      setErrors({});
      console.log("Form submitted:", { department, message, agreedToTerms });
    }
  }

  return (
    <form className="mt-4" onSubmit={handleSubmit}>
      <div className="mb-3">
        <label htmlFor="department" className="form-label">
          Department
        </label>
        <select
          id="department"
          className={`form-select ${errors.department ? "is-invalid" : ""}`}
          name="department"
          value={department}
          onChange={(e) => setDepartment(e.target.value)}
        >
          <option value="">Select...</option>
          <option value="hr">Human Resources</option>
          <option value="pr">Public Relations</option>
          <option value="support">Support</option>
        </select>
        {errors.department && (
          <div className="invalid-feedback">{errors.department}</div>
        )}
      </div>

      <div className="mb-3">
        <label htmlFor="message" className="form-label">
          Message
        </label>
        <textarea
          id="message"
          className={`form-control ${errors.message ? "is-invalid" : ""}`}
          name="message"
          value={message}
          onChange={(e) => setMessage(e.target.value)}
          cols="30"
          rows="5"
        />
        {errors.message && (
          <div className="invalid-feedback">{errors.message}</div>
        )}
      </div>

      <div className="mb-3 form-check">
        <input
          type="checkbox"
          id="agreedToTerms"
          className={`form-check-input ${
            errors.agreedToTerms ? "is-invalid" : ""
          }`}
          name="agreedToTerms"
          checked={agreedToTerms}
          onChange={(e) => setAgreedToTerms(e.target.checked)}
        />
        <label htmlFor="agreedToTerms" className="form-check-label">
          I agree to the terms and conditions.
        </label>
        {errors.agreedToTerms && (
          <div className="invalid-feedback">{errors.agreedToTerms}</div>
        )}
      </div>

      <button type="submit" className="btn btn-primary">
        Send
      </button>
    </form>
  );
}

function App() {
  return (
    <div className="container">
      <ContactUsForm />
    </div>
  );
}

ReactDOM.createRoot(document.getElementById("root")).render(<App />);
```

Here's the revised set of steps for the exercise, including the hint for using `useForm` directly and how to refactor the code:

---

## Exercise 10: Refactor Form with React Hook Form

**Objective:** Transition an existing form to use React Hook Form for managing form state and validation.

**Starter Code:** Start with the solution code from the prior exercise.

### Steps:

1. **Install React Hook Form:**
   Install React Hook Form using npm and include the UMD script in your `index.html`:

   ```html
   <script src="/node_modules/react-hook-form/dist/index.umd.js"></script>
   ```

   > It will need to be placed before `main.js`

2. **Import `useForm`:**
   Import `useForm` so that it can be called directly within the `ContactUsForm` component:

   ```javascript
   const { useForm } = ReactHookForm;
   ```

3. **Call `useForm`:**
   Call `useForm` inside your `ContactUsForm` component to manage form state:

   ```javascript
   const {
     register,
     handleSubmit,
     formState: { errors },
   } = useForm();
   ```

4. **Refactor Form Fields:**  
   Refactor each form field to use `register` from React Hook Form:

   - **Before:**
     ```javascript
     <select
       id="department"
       className={`form-select ${errors.department ? "is-invalid" : ""}`}
       name="department"
       value={department}
       onChange={(e) => setDepartment(e.target.value)}
     >
     ```
   - **After:**
     ```javascript
     <select
       id="department"
       className={`form-select ${errors.department ? "is-invalid" : ""}`}
       {...register("department", { required: "Department is required" })}
     >
     ```

5. **Refactor Validation Errors:**  
   Update the validation error messages to use React Hook Form’s `errors` object:

   - **Before:**
     ```javascript
     {
       errors.department && (
         <div className="invalid-feedback">{errors.department}</div>
       );
     }
     ```
   - **After:**
     ```javascript
     {
       errors.department && (
         <div className="invalid-feedback">{errors.department.message}</div>
       );
     }
     ```

<!-- 6. **Solution:**
   Once finished, your code should look like the following:

   ```html
   <!DOCTYPE html>
   <html lang="en">
     <head>
       <meta charset="UTF-8" />
       <meta name="viewport" content="width=device-width, initial-scale=1.0" />
       <title>React Demos</title>
       <link
         href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
         rel="stylesheet"
       />
       <link rel="stylesheet" href="styles.css" />
     </head>
     <body>
       <div id="root"></div>

       <script src="/node_modules/react/umd/react.development.js"></script>
       <script src="/node_modules/react-dom/umd/react-dom.development.js"></script>
       <script src="/node_modules/react-hook-form/dist/index.umd.js"></script>
       <script src="/node_modules/@babel/standalone/babel.min.js"></script>
       <script type="text/babel" src="/main.js"></script>
     </body>
   </html>
   ```

   ```javascript
   // main.js
   const { useForm } = ReactHookForm;

   function ContactUsForm() {
     const {
       register,
       handleSubmit,
       formState: { errors },
     } = useForm();

     function send(formData) {
       console.log("Form submitted:", formData);
     }

     return (
       <form className="mt-4" onSubmit={handleSubmit(register)}>
         <div className="mb-3">
           <label htmlFor="department" className="form-label">
             Department
           </label>
           <select
             id="department"
             className={`form-select ${errors.department ? "is-invalid" : ""}`}
             {...register("department", { required: "Department is required" })}
           >
             <option value="">Select...</option>
             <option value="hr">Human Resources</option>
             <option value="pr">Public Relations</option>
             <option value="support">Support</option>
           </select>
           {errors.department && (
             <div className="invalid-feedback">{errors.department.message}</div>
           )}
         </div>

         <div className="mb-3">
           <label htmlFor="message" className="form-label">
             Message
           </label>
           <textarea
             id="message"
             className={`form-control ${errors.message ? "is-invalid" : ""}`}
             {...register("message", { required: "Message is required" })}
             cols="30"
             rows="5"
           />
           {errors.message && (
             <div className="invalid-feedback">{errors.message.message}</div>
           )}
         </div>

         <div className="mb-3 form-check">
           <input
             type="checkbox"
             id="agreedToTerms"
             className={`form-check-input ${
               errors.agreedToTerms ? "is-invalid" : ""
             }`}
             {...register("agreedToTerms", {
               required: "You must agree to the terms to continue",
             })}
           />
           <label htmlFor="agreedToTerms" className="form-check-label">
             I agree to the terms and conditions.
           </label>
           {errors.agreedToTerms && (
             <div className="invalid-feedback">
               {errors.agreedToTerms.message}
             </div>
           )}
         </div>

         <button type="submit" className="btn btn-primary">
           Send
         </button>
       </form>
     );
   }

   function App() {
     return (
       <div className="container">
         <ContactUsForm />
       </div>
     );
   }

   ReactDOM.createRoot(document.getElementById("root")).render(<App />);
   ``` -->

## Exercise 11: Setting Up a REST API

In this exercise, you'll set up a REST API using `json-server` to simulate fetching data for an NBA teams application.

1. **Install `json-server`:**

   - Install `json-server` version 0.17.0 (to avoid using the beta version) by running the following command in your project directory:
     ```bash
     npm install json-server@0.17.0
     ```

2. **Create `db.json`:**

   - In your project directory, create a folder named `api`.
   - Inside the `api` folder, create a file named `db.json` and include the following content:
     ```json
     {
       "teams": [
         { "id": 1, "name": "Atlanta Hawks", "division": "Southeast" },
         { "id": 2, "name": "Boston Celtics", "division": "Atlantic" },
         { "id": 3, "name": "Brooklyn Nets", "division": "Atlantic" },
         { "id": 4, "name": "Charlotte Hornets", "division": "Southeast" },
         { "id": 5, "name": "Chicago Bulls", "division": "Central" },
         { "id": 6, "name": "Cleveland Cavaliers", "division": "Central" },
         { "id": 7, "name": "Dallas Mavericks", "division": "Southwest" },
         { "id": 8, "name": "Denver Nuggets", "division": "Northwest" },
         { "id": 9, "name": "Detroit Pistons", "division": "Central" },
         { "id": 10, "name": "Golden State Warriors", "division": "Pacific" },
         { "id": 11, "name": "Houston Rockets", "division": "Southwest" },
         { "id": 12, "name": "Indiana Pacers", "division": "Central" },
         { "id": 13, "name": "LA Clippers", "division": "Pacific" },
         { "id": 14, "name": "Los Angeles Lakers", "division": "Pacific" },
         { "id": 15, "name": "Memphis Grizzlies", "division": "Southwest" },
         { "id": 16, "name": "Miami Heat", "division": "Southeast" },
         { "id": 17, "name": "Milwaukee Bucks", "division": "Central" },
         {
           "id": 18,
           "name": "Minnesota Timberwolves",
           "division": "Northwest"
         },
         { "id": 19, "name": "New Orleans Pelicans", "division": "Southwest" },
         { "id": 20, "name": "New York Knicks", "division": "Atlantic" },
         { "id": 21, "name": "Oklahoma City Thunder", "division": "Northwest" },
         { "id": 22, "name": "Orlando Magic", "division": "Southeast" },
         { "id": 23, "name": "Philadelphia 76ers", "division": "Atlantic" },
         { "id": 24, "name": "Phoenix Suns", "division": "Pacific" },
         {
           "id": 25,
           "name": "Portland Trail Blazers",
           "division": "Northwest"
         },
         { "id": 26, "name": "Sacramento Kings", "division": "Pacific" },
         { "id": 27, "name": "San Antonio Spurs", "division": "Southwest" },
         { "id": 28, "name": "Toronto Raptors", "division": "Atlantic" },
         { "id": 29, "name": "Utah Jazz", "division": "Northwest" },
         { "id": 30, "name": "Washington Wizards", "division": "Southeast" }
       ]
     }
     ```

3. **Add a Script to Start `json-server`:**

   - In your project’s `package.json`, add a new script to start the `json-server`. Add this to the `"scripts"` section:
     ```json
     "scripts": {
       "api": "json-server --watch api/db.json --port 9000"
     }
     ```
   - This script starts the `json-server` on port 9000 and watches the `db.json` file for changes.

4. **Start the JSON Server:**

   - Open a new terminal window (leave `npm start` running) and run the following command in your project directory to start the server:
     ```bash
     npm run api
     ```

5. **Verify the Setup:**

   - Open your browser and navigate to `http://localhost:9000/teams` to see the list of NBA teams served by `json-server`. You should see a JSON response with all the teams.

With this setup, you now have a `json-server` instance running that provides a REST API for NBA teams.

## Exercise 12: GET from REST API

In this exercise, you will update the `teamAPI` to fetch data from a REST API served by `json-server` and handle errors gracefully using utility functions.

1. Starter Code:

   You will start with the following code in `main.js`:

   > This is the essentially the solution code from exercise 7 but it has been modified to use Bootstrap and include some helper functions for making HTTP calls

   ```js
   //main.js
   const { useState, useEffect } = React;

   const BASE_URL = "http://localhost:9000";

   function translateStatusToErrorMessage(status) {
     switch (status) {
       case 401:
         return "Please sign in again.";
       case 403:
         return "You do not have permission to view the data requested.";
       default:
         return "There was an error saving or retrieving data.";
     }
   }

   async function checkStatus(response) {
     if (response.ok) return response;

     const httpError = {
       status: response.status,
       statusText: response.statusText,
       url: response.url,
       body: await response.text(),
     };
     console.log(`http error status: ${JSON.stringify(httpError, null, 1)}`);

     let errorMessage = translateStatusToErrorMessage(httpError.status);
     throw new Error(errorMessage);
   }

   function parseJSON(response) {
     return response.json();
   }

   function delay(ms) {
     return function (x) {
       return new Promise((resolve) => setTimeout(() => resolve(x), ms));
     };
   }

   const url = `${BASE_URL}/teams`;
   const teamAPI = {
     list() {
       return new Promise((resolve) => {
         setTimeout(() => {
           resolve(nbaTeams);
         }, 1000);
       });
     },
   };

   function TeamList() {
     const [busy, setBusy] = useState(false);
     const [teams, setTeams] = useState([]);
     async function loadTeams() {
       setBusy(true);
       let data = await teamAPI.list();
       setBusy(false);
       setTeams(data);
     }

     useEffect(function () {
       loadTeams();
     }, []);

     return (
       <div className="list mt-2">
         {busy && <p>Loading...</p>}
         {teams?.map((team) => (
           <div className="card p-4" key={team.name}>
             <strong>{team.name}</strong>
             <div>{team.division}</div>
           </div>
         ))}
       </div>
     );
   }

   function App() {
     return (
       <div className="container">
         <TeamList />
       </div>
     );
   }

   ReactDOM.createRoot(document.getElementById("root")).render(<App />);
   ```

   ```css
   .list {
     display: flex;
     gap: 2rem;
     flex-wrap: wrap;
   }

   .card {
     width: 18rem;
   }
   ```

2. **Install Dependencies:**

- Ensure that you have `json-server` running on port 9000. If not, refer to Exercise 12 for the command to start it.
  > Note you will still need `npm start` running in a separate terminal to serve the front-end React code

3. **Update `teamAPI` to Use the REST API:**

- Modify the `teamAPI.list` function to fetch data from your `json-server` API.
- Use the provided functions `checkStatus` and `parseJSON` to handle the HTTP response and errors. Be sure to understand what they are doing and how to use them.

4. **Handle API Errors:**

- Update the `TeamList` component to display the error message if the API request fails. Use state to store and display any error messages.
  - The `error` that comes back from the API will have a `message` property which is what you will want to display

5. **Enhance the Component:**

- Ensure that the component displays loading status, fetches data from the REST API, and handles any errors appropriately.

6. **Verify the Application:**

- Run your application and verify that the NBA teams are fetched from the REST API and displayed correctly. Check for proper error handling and user messages.

#### Final Code Solution:

<!--
    ```js
    const { useState, useEffect } = React;

    const BASE_URL = "http://localhost:9000";

    function translateStatusToErrorMessage(status) {
      switch (status) {
        case 401:
          return "Please sign in again.";
        case 403:
          return "You do not have permission to view the data requested.";
        default:
          return "There was an error saving or retrieving data.";
      }
    }

    async function checkStatus(response) {
      if (response.ok) return response;

      const httpError = {
        status: response.status,
        statusText: response.statusText,
        url: response.url,
        body: await response.text(),
      };
      console.log(`http error status: ${JSON.stringify(httpError, null, 1)}`);

      let errorMessage = translateStatusToErrorMessage(httpError.status);
      throw new Error(errorMessage);
    }

    function parseJSON(response) {
      return response.json();
    }

    function delay(ms) {
      return function (x) {
        return new Promise((resolve) => setTimeout(() => resolve(x), ms));
      };
    }

    const url = `${BASE_URL}/teams`;
    const teamAPI = {
      list() {
        return fetch(url).then(checkStatus).then(parseJSON);
      },
    };

    function TeamList() {
      const [busy, setBusy] = useState(false);
      const [teams, setTeams] = useState([]);
      const [errorMessage, setErrorMessage] = useState(undefined);

      async function loadTeams() {
        try {
          setBusy(true);
          let data = await teamAPI.list();
          setBusy(false);
          setTeams(data);
        } catch (error) {
          setErrorMessage(error.message);
        } finally {
          setBusy(false);
        }
      }

      useEffect(function () {
        loadTeams();
      }, []);

      return (
        <div className="list mt-2">
          {errorMessage && <div className="alert alert-danger">{errorMessage}</div>}
          {busy && <p>Loading...</p>}
          {teams?.map((team) => (
            <div className="card p-4" key={team.name}>
              <strong>{team.name}</strong>
              <div>{team.division}</div>
            </div>
          ))}
        </div>
      );
    }

    function App() {
      return (
        <div className="container">
          <TeamList />
        </div>
      );
    }

    ReactDOM.createRoot(document.getElementById("root")).render(<App />);
    ``` -->
<!--
    #### HTML

  ```html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>React Demos</title>
      <link
        href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
        rel="stylesheet"
      />
      <link rel="stylesheet" href="styles.css" />
    </head>
    <body>
      <div id="root"></div>

      <script src="/node_modules/react/umd/react.development.js"></script>
      <script src="/node_modules/react-dom/umd/react-dom.development.js"></script>
      <script src="/node_modules/react-hook-form/dist/index.umd.js"></script>
      <script src="/node_modules/@babel/standalone/babel.min.js"></script>
      <script type="text/babel" src="/main.js"></script>
    </body>
  </html>
  ``` -->

<!-- #### CSS

```css
.list {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
}

.card {
  width: 18rem;
}
``` -->

---

## Exercise 13: Router

In this exercise, you'll set up routing in your React application using React Router. Follow the steps below to complete the exercise.

Here is a similar example to use as a reference. I would recommend not starting with this code but referencing it for syntax.

```js
//main.js

const {
  BrowserRouter: Router,
  Route,
  Routes,
  Link,
  NavLink,
  Navigate,
  useParams,
  useLocation,
  useNavigation,
} = window.ReactRouterDOM;

function HomePage() {
  return <h2>Home</h2>;
}

function AboutPage() {
  return <h2>About</h2>;
}

function ContactPage() {
  return <h2>Contact</h2>;
}

function App() {
  return (
    <Router>
      <div className="container">
        <nav className="my-4 mb-5">
          <ul className="nav nav-pills">
            <li className="nav-item">
              <NavLink className="nav-link" to="/">
                Home
              </NavLink>
            </li>
            <li className="nav-item">
              <NavLink className="nav-link" to="/about">
                About
              </NavLink>
            </li>
            <li className="nav-item">
              <NavLink className="nav-link" to="/contact">
                Contact
              </NavLink>
            </li>
          </ul>
        </nav>

        <div className="container">
          <Routes>
            <Route path="/" element={<HomePage />} />
            <Route path="about" element={<AboutPage />} />
            <Route path="contact" element={<ContactPage />} />
          </Routes>
        </div>
      </div>
    </Router>
  );
}

ReactDOM.createRoot(document.getElementById("root")).render(<App />);
```

```html
<!DOCTYPE html>
<!-- index.html -->
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>React Demos</title>
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
      rel="stylesheet"
    />
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <div id="root"></div>

    <script src="/node_modules/react/umd/react.development.js"></script>
    <script src="/node_modules/react-dom/umd/react-dom.development.js"></script>
    <script src="/node_modules/react-hook-form/dist/index.umd.js"></script>
    <script src="/node_modules/history/umd/history.development.js"></script>
    <script src="/node_modules/react-router/umd/react-router.development.js"></script>
    <script src="/node_modules/react-router-dom/umd/react-router-dom.development.js"></script>

    <script src="/node_modules/@babel/standalone/babel.min.js"></script>
    <script type="text/babel" src="/main.js"></script>
  </body>
</html>
```

### Steps:

1. **Install React Router**

   Ensure you have React Router installed. Run the following command to add it to your project:

   ```bash
   npm install react-router-dom
   ```

2. **Update `index.html`**

   Add the React Router script to your `index.html` file above the `main.js` script:

   ```html
   <script src="/node_modules/react-router-dom/umd/react-router-dom.development.js"></script>
   ```

3. **Create Components**

   Define three components for your pages: `HomePage`, `TeamsPage`, and `PlayersPage`. Each should return a simple `h2` element with the page name.

4. **Set Up Router**

   In your `App` component:

   - Import `BrowserRouter`, `Routes`, and `Route` from `react-router-dom`.
   - Wrap your component tree with `BrowserRouter`.
   - Use `Routes` and `Route` to define routes for `/`, `/teams`, and `/players`.

5. **Add Navigation**

   Create a navigation bar inside your `App` component:

   - Use `NavLink` from `react-router-dom` to create links for "Home", "Teams", and "Players".
   - Style the navigation bar using Bootstrap classes.

6. **Render the Application**

   Render the `App` component inside the `index.html` file.

7. **Verify the Application**

   Open your browser and navigate to the following URLs to verify that routing works as expected:

   - `/` should display the Home page.
   - `/teams` should display the Teams page.
   - `/players` should display the Players page.

   Ensure that the navigation links correctly switch between these pages and that the current page is highlighted in the navigation.

### Tips:

- Ensure `NavLink` is used to navigate between pages and applies the correct styling.
- Use the `element` prop in `Route` to render components for each route.

---

This guide provides step-by-step instructions, allowing students to build the routing setup and verify their implementation.

<!-- #### Solution Code

Here’s the final solution code for Exercise 14:

#### `main.js`

```js
const {
  BrowserRouter: Router,
  Route,
  Routes,
  Link,
  NavLink,
  Navigate,
  useParams,
  useLocation,
  useNavigation,
} = window.ReactRouterDOM;

function HomePage() {
  return <h2>Home</h2>;
}

function TeamsPage() {
  return <h2>Teams</h2>;
}

function PlayersPage() {
  return <h2>Players</h2>;
}

function App() {
  return (
    <Router>
      <div className="container">
        <nav className="my-4 mb-5">
          <ul className="nav nav-pills">
            <li className="nav-item">
              <NavLink className="nav-link" to="/">
                Home
              </NavLink>
            </li>
            <li className="nav-item">
              <NavLink className="nav-link" to="/teams">
                Teams
              </NavLink>
            </li>
            <li className="nav-item">
              <NavLink className="nav-link" to="/players">
                Players
              </NavLink>
            </li>
          </ul>
        </nav>

        <div className="container">
          <Routes>
            <Route path="/" element={<HomePage />} />
            <Route path="teams" element={<TeamsPage />} />
            <Route path="players" element={<PlayersPage />} />
          </Routes>
        </div>
      </div>
    </Router>
  );
}

ReactDOM.createRoot(document.getElementById("root")).render(<App />);
```

#### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>React Demos</title>
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
      rel="stylesheet"
    />
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <div id="root"></div>

    <script src="/node_modules/react/umd/react.development.js"></script>
    <script src="/node_modules/react-dom/umd/react-dom.development.js"></script>
    <script src="/node_modules/react-hook-form/dist/index.umd.js"></script>
    <script src="/node_modules/history/umd/history.development.js"></script>
    <script src="/node_modules/react-router/umd/react-router.development.js"></script>
    <script src="/node_modules/react-router-dom/umd/react-router-dom.development.js"></script>

    <script src="/node_modules/@babel/standalone/babel.min.js"></script>
    <script type="text/babel" src="/main.js"></script>
  </body>
</html>
``` -->

## Exercise 14: Route Parameters

1. Integrate the code from exercise 13 for the `TeamList` into `main.js` (this would include the movieAPI and the helper functions for calling it). Render the `TeamList` component inside of the `TeamsPage` component.
2. Add an **Add Team** link to the `TeamsPage` at the top next the **Teams** heading
   - use the React Router `Link` component and not a regular `a` tag
   - use the appropriate bootstrap classes to make the link look like a button
   - have the button go to a new route `teams/create` which we will create later
3. Create an `CreateTeamPage` component
   - it should just have a heading which contains **Add Team**
4. Add a `Route` to send `teams/create` to the `CreateTeamPage` component
5. Test to verify that the `Link` works correctly and takes the user to the new page component
6. Add an **Edit Team** link to each card in the `TeamsList`
   - use the React Router `Link` component and not a regular `a` tag
   - this should look like a link and not a Bootstrap button so no need to add any CSS classes
   - have the link go to a new route passing the team id of the current team, for example: `teams/edit/5`
7. Create an `EditTeamPage` component
   - it should just have a heading which contains **Edit Team**
8. Add a `Route` to send the url `teams/edit/:id` to the `EditTeamPage` component
9. Test to verify that the `Link` works correctly and takes the user to the edit page component

## Exercise 15: More Forms Practice

1. Create a `TeamForm` component
   - it should return a `form` tag and inside the form should be one label for **Team Name** and an input
2. Render the `TeamForm` inside both the `CreateTeamPage` and `EditTeamPage` components
3. Verify the form displays on each page
4. Add all the other needed form fields for a team based on the properties of the `team` object
5. Use React Hook Form to
   - Register each form field
   - Add a couple validation rules to the form as you see appropriate
   - Handle the submission of the form and log out the data
6. Verify the form data is logged and the validation displays error messages at the appropriate times

## Exercise 16

1. Add additional functions to the `teamAPI` object to insert and update the team data
2. Use the add(post) function in the `TeamForm`in the form submit event handler function to take the data from React Hook form and save it to the backend API.
3. Test the application to verify team insert works.
4. Use the update(put) function in the `TeamForm`in the form submit event handler function to take the data from React Hook form and save it to the backend API.
   - Tip: You can distinguish an insert from an update by looking to see if the team object has an id
     - if no `id` then insert else update
5. Test the application to verify team update works.
6. Redirect to the `TeamsPage` after a successful insert or update
