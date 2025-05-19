![image](https://github.com/PatrickFrankAIU/GradeManagerProject/assets/134087916/b5d814bf-e38f-456f-8f9c-cb5a98fb52fa)

# Cheat Sheet for Creating React Apps
## For students in the Full Stack Web Development program at Digital Crafts.    
Patrick Frank, Instructor

# React Cheat Sheet

## Creating a New App

- Start by making a folder and opening it in VS Code
- Open a terminal prompt and execute:
  ```bash
  npx create-react-app .
  ```
  - This may take a while, and you'll see things appear in Explorer
  - Done when it says "Happy hacking!"
- Now you're ready to run it:
  ```bash
  npm start
  ```
  - Note: The first time takes a little while, and messaging may pause in the terminal. Be patient!

## Development Workflow

At this point it's ready for development. Here are some tips:

- Main focus is `src/app.js`
- **Standard workflow:**
  1. Add a component (file) to src folder, such as `MyNewPage.js`
  2. Create a function within the file, then add the return statement with the JSX code:
     ```jsx
     function MyNewPage() {
       return (
         <div>
           <h1>Hello, this is MyNewPage!</h1>
         </div>
       );
     }
     ```
  3. Add the export statement:
     ```jsx
     export default MyNewPage;
     ```
  4. **Remember:** JSX gets wrapped in the parentheses of `return()`, which gets a semi-colon on the end!

- **Next:**
  1. Import the new file in app.js
     ```jsx
     import MyNewPage from './MyNewPage.js';
     ```
  2. Execute the new file in app.js's return() function
  3. Run the app

- Note: You can do all of the above while it's running, too.

## React Routing

To enable navigation between different pages/components:

1. Install React Router (stop first with control-C if currently running):
   ```bash
   npm install react-router-dom
   ```

2. Set up your router in `App.js`:
   ```jsx
   import { BrowserRouter, Routes, Route } from 'react-router-dom';
   import Home from './Home';
   import About from './About';
   import Navbar from './Navbar';

   function App() {
     return (
       <BrowserRouter>
         <Navbar />
         <Routes>
           <Route path="/" element={<Home />} />
           <Route path="/about" element={<About />} />
         </Routes>
       </BrowserRouter>
     );
   }
   ```

3. Create a navigation component (`Navbar.js`):
   ```jsx
   import { Link } from 'react-router-dom';

   function Navbar() {
     return (
       <nav>
         <Link to="/">Home</Link>
         <Link to="/about">About</Link>
       </nav>
     );
   }

   export default Navbar;
   ```

4. Navigate programmatically (e.g., after form submission):
   ```jsx
   import { useNavigate } from 'react-router-dom';

   function LoginForm() {
     const navigate = useNavigate();
     
     const handleSubmit = (e) => {
       e.preventDefault();
       // Process login...
       navigate('/dashboard');
     };
     
     return (
       <form onSubmit={handleSubmit}>
         {/* form fields */}
         <button type="submit">Login</button>
       </form>
     );
   }
   ```

5. Access URL parameters:
   ```jsx
   // In App.js route definition
   <Route path="/product/:id" element={<ProductDetail />} />

   // In ProductDetail.js
   import { useParams } from 'react-router-dom';

   function ProductDetail() {
     const { id } = useParams();
     return <h1>Product ID: {id}</h1>;
   }
   ```

## Useful Resources

### Geeks4Geeks (good tutorial): https://www.geeksforgeeks.org/react/
- Good starting tutorial
- Excellent overview of JSX, components, Redux, Hooks, and DOM events
- Solid look at Routing (navigation) and component lifecycles
- Check out the potential interview questions!

## CRA Alternatives

Note: CRA ("create-react-app") has been deprecated.
- Still works, but less popular today
- There's a standard NPM package, but it requires additional configuration (cumbersome)
- I recommend continuing to use CRA, which is NOT going away and is still recommended for educational use

### Vite
- An alternative to CRA
- Uses esbuild instead of webpack
- Recommended and widely used
- Setup:
  ```bash
  npm create vite@latest .
  ```
  - Those colorful menus during the creation scripts are intended to be navigated using the arrow keys!
  - Then do `npm install` (picks up node and more)
  - Then do `npm run dev` to run
    - Have to control-click the link in the terminal
    - Can auto-start by adding "--open" after dev in package.json
- Uses the same approach of modules and imports, but there are some confusing differences
- **Suggestion:** Wait until you are more familiar with React before embracing Vite
