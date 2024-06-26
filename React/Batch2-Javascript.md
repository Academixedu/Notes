1. Variables and Constants

JavaScript uses `let` and `const` for declaring variables:

```javascript
let movieTitle = "Inception";  // Can be reassigned
const releaseYear = 2010;      // Cannot be reassigned
```

2. Functions

Functions are blocks of reusable code:

```javascript
function displayMovie(title, year) {
  console.log(`${title} (${year})`);
}

displayMovie("The Matrix", 1999);
```

3. Arrow Functions

A more concise way to write functions:

```javascript
const displayMovie = (title, year) => {
  console.log(`${title} (${year})`);
};

displayMovie("Interstellar", 2014);
```

4. Arrays and Array Methods

Arrays store collections of data:

```javascript
const movies = ["Inception", "The Matrix", "Interstellar"];

// forEach to iterate
movies.forEach(movie => console.log(movie));

// map to transform
const upperCaseMovies = movies.map(movie => movie.toUpperCase());

// filter to select
const moviesWithI = movies.filter(movie => movie.startsWith("I"));
```

5. Objects

Objects store key-value pairs:

```javascript
const movie = {
  title: "Inception",
  year: 2010,
  director: "Christopher Nolan"
};

console.log(movie.title);  // Accessing a property
```

6. Destructuring

Extracting values from objects or arrays:

```javascript
const { title, year } = movie;
console.log(title);  // "Inception"

const [firstMovie, secondMovie] = movies;
console.log(firstMovie);  // "Inception"
```

7. Template Literals

For string interpolation:

```javascript
const movieInfo = `${movie.title} was released in ${movie.year}`;
console.log(movieInfo);
```

8. Promises and Async/Await

For handling asynchronous operations:

```javascript
// Promise
function fetchMoviePromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve("Inception"), 1000);
  });
}

fetchMoviePromise().then(movie => console.log(movie));

// Async/Await
async function fetchMovie() {
  const movie = await fetchMoviePromise();
  console.log(movie);
}

fetchMovie();
```

9. Modules (Import/Export)

For organizing code into reusable files:

```javascript
// In movieUtils.js
export const formatMovie = (title, year) => `${title} (${year})`;

// In main.js
import { formatMovie } from './movieUtils.js';
console.log(formatMovie("Inception", 2010));
```

10. Error Handling

Using try/catch for handling errors:

```javascript
async function fetchMovie() {
  try {
    const response = await fetch('https://api.example.com/movies/1');
    const movie = await response.json();
    console.log(movie);
  } catch (error) {
    console.error('Error fetching movie:', error);
  }
}
```

