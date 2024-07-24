#### Basic react app ####
Install Nodejs 
npx create-react-app myapp
cd myapp
npm start

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
####################################
