![image](https://github.com/PatrickFrankAIU/GradeManagerProject/assets/134087916/b5d814bf-e38f-456f-8f9c-cb5a98fb52fa)

## For students in the Full Stack Web Development program at Digital Crafts.    
_Note: This document assumes that you are already familiar with Node and Visual Studio Code!_

Author: Patrick Frank, Instructor
For more information, please contact me at pfrank@aiuniv.edu

# React Cheat Sheet

## Table of Contents
- [Creating a New App](#creating-a-new-app)
- [Development Workflow](#development-workflow)
- [React Routing](#react-routing)
- [Deployment with GitHub and Render.com](#deployment-with-github-and-rendercom)
- [Useful Resources](#useful-resources)
- [CRA Alternatives](#cra-alternatives)

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

1. Install React Router:
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

## Deployment with GitHub and Render.com

### GitHub Repository Setup

If you've created your React app in VS Code:

1. In VS Code:
   - Click on the Source Control icon in the sidebar (branch icon)
   - Click "Publish to GitHub"
   - Choose "Public" or "Private" repository
   - Name your repository and click "OK"

2. Verify your code is now on GitHub by visiting your GitHub profile

### Deploying with Render.com

Assuming your Render account is connected to your GitHub account:

1. Log in to Render.com

2. Click "New" and select "Web Service"

3. Find and select your GitHub repository

4. Configure your web service:
   - **Name**: Your project name
   - **Runtime**: Node
   - **Build Command**: `npm run build`
   - **Start Command**: `serve -s build` (You might need to install serve: `npm install -g serve`)

5. Click "Create Web Service"

6. Once deployed, Render will provide you with a URL to access your live application

7. For future updates:
   - Push changes to GitHub
   - Render will automatically rebuild and redeploy your application

That's it! Your React app is now live on the internet.

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
- An alternative to CRA, made by the same guy who made Vue
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

[Return to Top](#react-cheat-sheet)
