

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
```javascript
// Promise
function fetchMoviePromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve("Inception"), 1000);
  });
}
fetchMoviePromise().then(movie => console.log("Promise result:", movie));

// Async/Await
async function fetchMovie() {
  const movie = await fetchMoviePromise();
  console.log("Async/Await result:", movie);
}
fetchMovie();

console.log("This will appear before the Promise and Async/Await results");
```
Expected output (after 1 second):
```
This will appear before the Promise and Async/Await results
Promise result: Inception
Async/Await result: Inception
```

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
