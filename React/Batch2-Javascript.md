

1. Variables and Constants
```javascript
let movieTitle = "Inception";  // Can be reassigned
const releaseYear = 2010;      // Cannot be reassigned

console.log(movieTitle);
console.log(releaseYear);
```
Expected output:
```
Inception
2010
```

2. Functions
```javascript
function displayMovie(title, year) {
  console.log(`${title} (${year})`);
}
displayMovie("The Matrix", 1999);
```
Expected output:
```
The Matrix (1999)
```

3. Arrow Functions
```javascript
const displayMovie = (title, year) => {
  console.log(`${title} (${year})`);
};
displayMovie("Interstellar", 2014);
```
Expected output:
```
Interstellar (2014)
```

4. Arrays and Array Methods
```javascript
const movies = ["Inception", "The Matrix", "Interstellar"];
// forEach to iterate
console.log("forEach output:");
movies.forEach(movie => console.log(movie));

```
Expected output:
```
forEach output:
Inception
The Matrix
Interstellar

```

5. Objects
```javascript
const movie = {
  title: "Inception",
  year: 2010,
  director: "Christopher Nolan"
};
console.log(movie.title);  // Accessing a property
console.log(movie.year);
console.log(movie.director);
```
Expected output:
```
Inception
2010
Christopher Nolan
```

6. Destructuring
```javascript
const { title, year } = movie;
console.log(title);
console.log(year);

const [firstMovie, secondMovie] = movies;
console.log(firstMovie);
console.log(secondMovie);
```
Expected output:
```
Inception
2010
Inception
The Matrix
```

7. Template Literals
```javascript
const movieInfo = `${movie.title} was released in ${movie.year}`;
console.log(movieInfo);
```
Expected output:
```
Inception was released in 2010
```

8. Promises and Async/Await


First, let's create some helper functions to simulate API calls:

```javascript
function fetchUserData(userId) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve({ id: userId, name: "John Doe" });
    }, 1000);
  });
}

function fetchUserPosts(userId) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve([
        { id: 1, title: "First post" },
        { id: 2, title: "Second post" }
      ]);
    }, 1000);
  });
}
```

Now, let's implement the program without async/await:

```javascript
// Without async/await
function getUserInfo(userId) {
  console.log("Fetching user data...");
  fetchUserData(userId)
    .then((user) => {
      console.log("User:", user);
      console.log("Fetching user posts...");
      return fetchUserPosts(userId);
    })
    .then((posts) => {
      console.log("User posts:", posts);
      console.log("Task complete!");
    })
    .catch((error) => {
      console.error("Error:", error);
    });
}

console.log("Starting without async/await");
getUserInfo(1);
console.log("Function called");
```

Now, let's implement the same program with async/await:

```javascript
// With async/await
async function getUserInfoAsync(userId) {
  try {
    console.log("Fetching user data...");
    const user = await fetchUserData(userId);
    console.log("User:", user);

    console.log("Fetching user posts...");
    const posts = await fetchUserPosts(userId);
    console.log("User posts:", posts);

    console.log("Task complete!");
  } catch (error) {
    console.error("Error:", error);
  }
}

console.log("Starting with async/await");
getUserInfoAsync(1);
console.log("Function called");
```

To see the difference, you can run both versions:

```javascript
// Run both versions
console.log("Running without async/await:");
getUserInfo(1);

setTimeout(() => {
  console.log("\nRunning with async/await:");
  getUserInfoAsync(1);
}, 3000);
```

The output will be similar for both, but the key differences are:

1. Code structure: The async/await version looks more like synchronous code, making it easier to read and understand the flow.

2. Error handling: In the async/await version, we use a try/catch block, which is more similar to synchronous error handling.

3. Chaining: The Promise version uses .then() chaining, while the async/await version uses normal sequential code.

Both versions will output:

```
Starting
Fetching user data...
Function called
User: { id: 1, name: 'John Doe' }
Fetching user posts...
User posts: [ { id: 1, title: 'First post' }, { id: 2, title: 'Second post' } ]
Task complete!
```

The main advantage of async/await is that it allows you to write asynchronous code that looks and behaves more like synchronous code, making it easier to understand and maintain, especially for more complex operations.

9. Modules (Import/Export)
Assuming we have two files:

movieUtils.js:
```javascript
export const formatMovie = (title, year) => `${title} (${year})`;
```

main.js:
```javascript
import { formatMovie } from './movieUtils.js';
console.log(formatMovie("Inception", 2010));
```
Expected output when running main.js:
```
Inception (2010)
```

10. Error Handling
```javascript
async function fetchMovie() {
  try {
    const response = await fetch('https://api.example.com/movies/1');
    const movie = await response.json();
    console.log("Fetched movie:", movie);
  } catch (error) {
    console.error('Error fetching movie:', error);
  }
}
fetchMovie();
```
Expected output (assuming the fetch fails):
```
Error fetching movie: TypeError: Failed to fetch
```

.
