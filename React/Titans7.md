#### Basic react app ####
```
Install Nodejs 
npx create-react-app myapp
cd myapp
npm start
```
### Step 2: Introduction to HTML/CSS

#### Basic HTML Structure

1. **Creating a Simple HTML Page:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My First HTML Page</title>
</head>
<body>
  <h1>Welcome to My Website</h1>
  <p>This is a paragraph of text on my first web page.</p>
  <a href="https://www.example.com">Visit Example.com</a>
</body>
</html>
```

2. **CSS Basics:**

#### Linking CSS to HTML

1. **Inline CSS:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Inline CSS Example</title>
</head>
<body>
  <p style="color: red;">This is a red paragraph.</p>
</body>
</html>
```

2. **Internal CSS:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Internal CSS Example</title>
  <style>
    body {
      background-color: lightblue;
    }
    p {
      color: green;
    }
  </style>
</head>
<body>
  <p>This is a green paragraph on a light blue background.</p>
</body>
</html>
```

3. **External CSS:**

**styles.css:**

```css
body {
  background-color: lightblue;
}
p {
  color: blue;
}
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>External CSS Example</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <p>This is a blue paragraph on a light blue background.</p>
</body>
</html>
```

#### Basic CSS Properties

1. **Color and Background:**

```css
body {
  background-color: lightblue;
}
p {
  color: red;
}
```

2. **Text Styling:**

```css
h1 {
  font-family: Arial, sans-serif;
  font-size: 24px;
  text-align: center;
}
```

3. **Box Model:**

```css
div {
  margin: 10px;
  border: 1px solid black;
  padding: 5px;
  width: 200px;
}
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Box Model Example</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div>This is a box model example.</div>
</body>
</html>
```

#### Selectors

1. **Type Selector:**

```css
p {
  color: blue;
}
```

2. **Class Selector:**

**styles.css:**

```css
.classname {
  color: green;
}
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Class Selector Example</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <p class="classname">This is a green paragraph.</p>
</body>
</html>
```

3. **ID Selector:**

**styles.css:**

```css
#idname {
  color: orange;
}
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ID Selector Example</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <p id="idname">This is an orange paragraph.</p>
</body>
</html>
```

#### Responsive Design

1. **Media Queries:**

**styles.css:**

```css
body {
  background-color: lightblue;
}
@media (max-width: 600px) {
  body {
    background-color: lightgreen;
  }
}
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Design Example</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <p>Resize the browser window to see the background color change.</p>
</body>
</html>
```

2. **Flexible Layouts:**

**styles.css:**

```css
.container {
  display: flex;
  flex-direction: column;
}
@media (min-width: 600px) {
  .container {
    flex-direction: row;
  }
}
.box {
  margin: 10px;
  padding: 10px;
  background-color: lightcoral;
  flex: 1;
}
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Flexible Layout Example</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
    <div class="box">Box 3</div>
  </div>
</body>
</html>
```

### Practical Examples and Exercises

1. **Create a Simple Web Page:**

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Simple Web Page</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
      color: #333;
      text-align: center;
      padding: 50px;
    }
    h1 {
      color: #ff6347;
    }
    p {
      font-size: 18px;
    }
  </style>
</head>
<body>
  <h1>Welcome to My Simple Web Page</h1>
  <p>This page demonstrates basic HTML and CSS.</p>
</body>
</html>
```

2. **Styling Text and Boxes:**

**styles.css:**

```css
body {
  font-family: Arial, sans-serif;
}
h1 {
  color: #4CAF50;
  text-align: center;
}
p {
  font-size: 20px;
  color: #555;
}
.box {
  margin: 20px;
  border: 2px solid #000;
  padding: 10px;
  width: 300px;
  background-color: #f9f9f9;
}
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Styling Text and Boxes</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <h1>Styling Text and Boxes</h1>
  <p>This example shows how to style text and boxes using CSS.</p>
  <div class="box">This is a styled box.</div>
</body>
</html>
```

3. **Responsive Design Practice:**

**styles.css:**

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  color: #333;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.box {
  margin: 10px;
  padding: 20px;
  background-color: #ffcccb;
  flex: 1;
  width: 80%;
  max-width: 600px;
}
@media (min-width: 600px) {
  .container {
    flex-direction: row;
  }
  .box {
    width: auto;
  }
}
```

**index.html:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Design Practice</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="

container">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
    <div class="box">Box 3</div>
  </div>
</body>
</html>
```
#####################excercise ######################
# HTML/CSS Tutorial: Building a Personal Portfolio

This tutorial will guide you through creating a simple personal portfolio page, introducing HTML and CSS concepts step-by-step.

## Step 1: Basic HTML Structure

Create a file named `index.html` and add the following basic HTML structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
</head>
<body>
    <h1>Welcome to My Portfolio</h1>
    <p>This is a simple portfolio page.</p>
</body>
</html>
```

Save the file and open it in a web browser to see the result.

## Step 2: Adding More Content

Let's add more content to our page. Update the `<body>` section of your HTML:

```html
<body>
    <header>
        <h1>John Doe</h1>
        <p>Web Developer</p>
    </header>
    
    <nav>
        <ul>
            <li><a href="#about">About</a></li>
            <li><a href="#projects">Projects</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>
    
    <main>
        <section id="about">
            <h2>About Me</h2>
            <p>I'm a passionate web developer with experience in HTML, CSS, and JavaScript.</p>
        </section>
        
        <section id="projects">
            <h2>My Projects</h2>
            <ul>
                <li>Project 1</li>
                <li>Project 2</li>
                <li>Project 3</li>
            </ul>
        </section>
        
        <section id="contact">
            <h2>Contact Me</h2>
            <p>Email: john.doe@example.com</p>
        </section>
    </main>
    
    <footer>
        <p>&copy; 2024 John Doe. All rights reserved.</p>
    </footer>
</body>
```

## Step 3: Introduction to CSS

Now, let's add some basic styling. In the `<head>` section of your HTML, add a `<style>` tag:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
        }
        header {
            background-color: #35424a;
            color: white;
            text-align: center;
            padding: 1rem;
        }
        nav ul {
            list-style-type: none;
            padding: 0;
        }
        nav ul li {
            display: inline;
            margin-right: 10px;
        }
        nav a {
            color: #35424a;
            text-decoration: none;
        }
        main {
            padding: 20px;
        }
        footer {
            background-color: #35424a;
            color: white;
            text-align: center;
            padding: 1rem;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
```

## Step 4: Responsive Design

Let's make our page responsive. Add the following CSS to your `<style>` tag:

```css
@media (max-width: 600px) {
    nav ul li {
        display: block;
        margin-bottom: 10px;
    }
}
```

## Step 5: Adding More Styles

Let's enhance our design further. Update your CSS in the `<style>` tag:

```css
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
    color: #333;
}
header {
    background-color: #35424a;
    color: white;
    text-align: center;
    padding: 2rem;
}
header h1 {
    margin-bottom: 0;
}
nav {
    background-color: #fff;
    padding: 1rem;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
nav ul {
    list-style-type: none;
    padding: 0;
    text-align: center;
}
nav ul li {
    display: inline;
    margin-right: 20px;
}
nav a {
    color: #35424a;
    text-decoration: none;
    font-weight: bold;
    transition: color 0.3s ease;
}
nav a:hover {
    color: #e74c3c;
}
main {
    max-width: 800px;
    margin: 20px auto;
    padding: 20px;
    background-color: white;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
}
section {
    margin-bottom: 30px;
}
h2 {
    color: #35424a;
    border-bottom: 2px solid #e74c3c;
    padding-bottom: 10px;
}
footer {
    background-color: #35424a;
    color: white;
    text-align: center;
    padding: 1rem;
    position: fixed;
    bottom: 0;
    width: 100%;
}

@media (max-width: 600px) {
    nav ul li {
        display: block;
        margin-bottom: 10px;
    }
    main {
        padding: 10px;
    }
}
```

## Final Result

You now have a beautiful, responsive personal portfolio page! Here's what you've learned:

1. Basic HTML structure
2. Semantic HTML elements (header, nav, main, section, footer)
3. CSS styling (colors, fonts, layout)
4. Responsive design with media queries
5. CSS transitions for interactive elements

Feel free to customize the content, colors, and styles to make it your own. You can also continue to enhance this page by adding images, more detailed project descriptions, or even a contact form.

##############
```
Git concepts..

mkdir my-git-repo
cd my-git-repo
git init

echo "First line" > myfile.txt
git add myfile.txt
git commit -m "Add first line"

echo "Second line" >> myfile.txt
git add myfile.txt
git commit -m "Add second line"

echo "Third line" >> myfile.txt
git add myfile.txt
git commit -m "Add third line"

git tag v1.0.0

git reset --hard v1.0.0

echo "Fourth line" >> myfile.txt
git add myfile.txt
git commit -m "Add fourth line"

echo "Fifth line" >> myfile.txt
git add myfile.txt
git commit -m "Add fifth line"

git checkout v1.0.0

git checkout main
```
####################################

Based on the image and your request to teach building this website using MUI (Material-UI) with React, I'd suggest the following plan:



```tsx
import React from 'react';
import { ThemeProvider, createTheme } from '@mui/material/styles';
import CssBaseline from '@mui/material/CssBaseline';
import Box from '@mui/material/Box';
import Header from './components/Header';
import Sidebar from './components/Sidebar';
import MovieList from './components/MovieList';
import FeaturedMovie from './components/FeaturedMovie';

const theme = createTheme({
  palette: {
    mode: 'dark',
    primary: {
      main: '#1976d2',
    },
  },
});

const App = () => {
  return (
    <ThemeProvider theme={theme}>
      <CssBaseline />
      <Box sx={{ display: 'flex' }}>
        <Header />
        <Sidebar />
        <Box component="main" sx={{ flexGrow: 1, p: 3 }}>
          <FeaturedMovie />
          <MovieList />
        </Box>
      </Box>
    </ThemeProvider>
  );
};

export default App;

```

### MUI Versus HTML/CSS

# Material-UI (MUI) Tutorial with HTML and CSS

## Introduction

Material-UI (MUI) is a popular React UI framework that implements Google's Material Design. This tutorial will guide you through creating a simple webpage using MUI components while also showing equivalent HTML/CSS implementations for comparison.

## Prerequisites

- Basic knowledge of HTML, CSS, and JavaScript
- Node.js and npm installed on your computer
- A code editor (e.g., Visual Studio Code)

## Step 1: Setting up the project

1. Create a new React project:
   ```
   npx create-react-app mui-tutorial
   cd mui-tutorial
   ```

2. Install MUI:
   ```
   npm install @mui/material @emotion/react @emotion/styled
   ```

3. Open the project in your code editor.

## Step 2: Creating a Basic Layout

Let's start by creating a basic layout with a header, main content, and a sidebar.

### HTML/CSS Version

Create a new file called `index.html` in the `public` folder:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MUI Tutorial</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }
        header {
            background-color: #1976d2;
            color: white;
            padding: 1rem;
        }
        main {
            display: flex;
            flex: 1;
        }
        aside {
            background-color: #f0f0f0;
            width: 200px;
            padding: 1rem;
        }
        .content {
            flex: 1;
            padding: 1rem;
        }
    </style>
</head>
<body>
    <header>
        <h1>My Website</h1>
    </header>
    <main>
        <aside>
            <h2>Sidebar</h2>
            <ul>
                <li>Link 1</li>
                <li>Link 2</li>
                <li>Link 3</li>
            </ul>
        </aside>
        <div class="content">
            <h2>Main Content</h2>
            <p>This is the main content area.</p>
        </div>
    </main>
</body>
</html>
```

### MUI Version

Now, let's create the same layout using MUI components. Replace the content of `src/App.js` with:

```jsx
import React from 'react';
import { AppBar, Toolbar, Typography, Container, Grid, Paper } from '@mui/material';

function App() {
  return (
    <div>
      <AppBar position="static">
        <Toolbar>
          <Typography variant="h6">
            My Website
          </Typography>
        </Toolbar>
      </AppBar>
      <Container>
        <Grid container spacing={3} style={{ marginTop: '20px' }}>
          <Grid item xs={12} md={3}>
            <Paper style={{ padding: '20px' }}>
              <Typography variant="h6">Sidebar</Typography>
              <ul>
                <li>Link 1</li>
                <li>Link 2</li>
                <li>Link 3</li>
              </ul>
            </Paper>
          </Grid>
          <Grid item xs={12} md={9}>
            <Paper style={{ padding: '20px' }}>
              <Typography variant="h5">Main Content</Typography>
              <Typography>This is the main content area.</Typography>
            </Paper>
          </Grid>
        </Grid>
      </Container>
    </div>
  );
}

export default App;
```

## Step 3: Adding a Button

Let's add a button to our layout to see how MUI handles interactive elements.

### HTML/CSS Version

Add the following to your `index.html` file, inside the `<div class="content">`:

```html
<button style="background-color: #1976d2; color: white; border: none; padding: 10px 20px; cursor: pointer;">
  Click me!
</button>
```

### MUI Version

In your `App.js` file, import the Button component:

```jsx
import { ..., Button } from '@mui/material';
```

Then add the Button to your main content area:

```jsx
<Paper style={{ padding: '20px' }}>
  <Typography variant="h5">Main Content</Typography>
  <Typography>This is the main content area.</Typography>
  <Button variant="contained" color="primary" style={{ marginTop: '20px' }}>
    Click me!
  </Button>
</Paper>
```

## Step 4: Creating a Form

Forms are a common part of web applications. Let's create a simple form to see how MUI handles form elements.

### HTML/CSS Version

Add the following to your `index.html` file, inside the `<div class="content">`:

```html
<form style="margin-top: 20px;">
  <div style="margin-bottom: 10px;">
    <label for="name" style="display: block; margin-bottom: 5px;">Name:</label>
    <input type="text" id="name" name="name" style="width: 100%; padding: 5px;">
  </div>
  <div style="margin-bottom: 10px;">
    <label for="email" style="display: block; margin-bottom: 5px;">Email:</label>
    <input type="email" id="email" name="email" style="width: 100%; padding: 5px;">
  </div>
  <button type="submit" style="background-color: #1976d2; color: white; border: none; padding: 10px 20px; cursor: pointer;">
    Submit
  </button>
</form>
```

### MUI Version

In your `App.js` file, import the necessary components:

```jsx
import { ..., TextField } from '@mui/material';
```

Then add the form to your main content area:

```jsx
<Paper style={{ padding: '20px' }}>
  <Typography variant="h5">Main Content</Typography>
  <Typography>This is the main content area.</Typography>
  <form style={{ marginTop: '20px' }}>
    <TextField
      fullWidth
      label="Name"
      variant="outlined"
      margin="normal"
    />
    <TextField
      fullWidth
      label="Email"
      variant="outlined"
      margin="normal"
      type="email"
    />
    <Button type="submit" variant="contained" color="primary" style={{ marginTop: '20px' }}>
      Submit
    </Button>
  </form>
</Paper>
```

## Conclusion

This tutorial has introduced you to the basics of using Material-UI components while comparing them to traditional HTML and CSS implementations. MUI provides a consistent design language and pre-built components that can significantly speed up your development process.

As you continue learning, explore more MUI components and features like theming, responsive design, and advanced customization options.

This structure sets up the basic layout of the application. Let's break down the next steps:

1. Header Component:
   - Create a new file `Header.js` in a `components` folder.
   - Implement an AppBar from MUI with a logo, search input, and login button.

2. Sidebar Component:
   - Create `Sidebar.js` in the `components` folder.
   - Use MUI's Drawer component to create a sidebar with categories and genres.

3. FeaturedMovie Component:
   - Create `FeaturedMovie.js` for the large banner at the top.
   - Use MUI's Card or custom styling to create the featured movie section.

4. MovieList Component:
   - Create `MovieList.js` to display the grid of movie posters.
   - Use MUI's Grid and Card components to create a responsive layout.

5. Implement Routing:
   - Install `react-router-dom`
   - Set up routes for different pages (e.g., home, movie details, categories)

6. State Management:
   - Consider using React Context or Redux for managing global state (e.g., selected genres, search queries)

7. API Integration:
   - Set up API calls to fetch movie data (you can use a mock API or a real movie database API)

8. Responsive Design:
   - Utilize MUI's responsive utilities to ensure the app looks good on all device sizes

9. Theme Customization:
   - Customize the MUI theme to match the blue color scheme in the image


