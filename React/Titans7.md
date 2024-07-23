
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

