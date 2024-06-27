To add movies from TMDB (The Movie Database) to your current implementation, you'll need to follow these steps:

1. Set up TMDB API:
   - Sign up for a TMDB account and get an API key
   - Create a configuration file for your API key

2. Create a new service to fetch movies from TMDB

3. Update your Redux store to handle movie data

4. Create actions and reducers for fetching movies

5. Update your components to display the fetched movies

Let's go through these steps:

1. Set up TMDB API:
   Create a file named `tmdbConfig.js` in your `src` folder:

```javascript
// src/tmdbConfig.js
export const TMDB_API_KEY = 'your_api_key_here';
export const TMDB_BASE_URL = 'https://api.themoviedb.org/3';
```

2. Create a new service to fetch movies:
   Create a file named `tmdbApi.js` in your `src/services` folder:

```javascript
// src/services/tmdbApi.js
import axios from 'axios';
import { TMDB_API_KEY, TMDB_BASE_URL } from '../tmdbConfig';

const tmdbApi = axios.create({
  baseURL: TMDB_BASE_URL,
  params: {
    api_key: TMDB_API_KEY,
  },
});

export const getMovies = async (type = 'popular', page = 1) => {
  try {
    const response = await tmdbApi.get(`/movie/${type}`, {
      params: { page },
    });
    return response.data;
  } catch (error) {
    console.error('Error fetching movies:', error);
    return null;
  }
};

export default tmdbApi;
```

3. Update Redux store:
   If you haven't set up Redux yet, you'll need to install it:

```
npm install redux react-redux @reduxjs/toolkit
```

Then create a store file:

```javascript
// src/store/store.js
import { configureStore } from '@reduxjs/toolkit';
import moviesReducer from './moviesSlice';

export const store = configureStore({
  reducer: {
    movies: moviesReducer,
  },
});
```

4. Create actions and reducers:
   Create a file named `moviesSlice.js` in your `src/store` folder:

```javascript
// src/store/moviesSlice.js
import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';
import { getMovies } from '../services/tmdbApi';

export const fetchMovies = createAsyncThunk(
  'movies/fetchMovies',
  async ({ type, page }, thunkAPI) => {
    const response = await getMovies(type, page);
    return response.results;
  }
);

const moviesSlice = createSlice({
  name: 'movies',
  initialState: {
    list: [],
    status: 'idle',
    error: null,
  },
  reducers: {},
  extraReducers: (builder) => {
    builder
      .addCase(fetchMovies.pending, (state) => {
        state.status = 'loading';
      })
      .addCase(fetchMovies.fulfilled, (state, action) => {
        state.status = 'succeeded';
        state.list = action.payload;
      })
      .addCase(fetchMovies.rejected, (state, action) => {
        state.status = 'failed';
        state.error = action.error.message;
      });
  },
});

export default moviesSlice.reducer;
```

5. Update components:
   Create a new component to display movies:

```javascript
// src/components/MovieList.js
import React, { useEffect } from 'react';
import { useDispatch, useSelector } from 'react-redux';
import { fetchMovies } from '../store/moviesSlice';
import { Grid, Card, CardMedia, CardContent, Typography } from '@mui/material';

const MovieList = () => {
  const dispatch = useDispatch();
  const { list: movies, status, error } = useSelector((state) => state.movies);

  useEffect(() => {
    if (status === 'idle') {
      dispatch(fetchMovies({ type: 'popular', page: 1 }));
    }
  }, [status, dispatch]);

  if (status === 'loading') return <div>Loading...</div>;
  if (status === 'failed') return <div>Error: {error}</div>;

  return (
    <Grid container spacing={3}>
      {movies.map((movie) => (
        <Grid item xs={12} sm={6} md={4} lg={3} key={movie.id}>
          <Card>
            <CardMedia
              component="img"
              height="140"
              image={`https://image.tmdb.org/t/p/w500${movie.poster_path}`}
              alt={movie.title}
            />
            <CardContent>
              <Typography gutterBottom variant="h6" component="div">
                {movie.title}
              </Typography>
              <Typography variant="body2" color="text.secondary">
                {movie.release_date}
              </Typography>
            </CardContent>
          </Card>
        </Grid>
      ))}
    </Grid>
  );
};

export default MovieList;
```

Finally, update your `App.js` to include the `MovieList` component:

```javascript
import React from "react";
import { Box } from "@mui/material";
import ButtonAppBar from "./AppBar";
import PermanentDrawerLeft from "./PermanentDrawer";
import MovieList from "./components/MovieList";
import { Provider } from 'react-redux';
import { store } from './store/store';

function App() {
  return (
    <Provider store={store}>
      <Box sx={{ display: "flex" }}>
        <ButtonAppBar />
        <PermanentDrawerLeft />
        <Box component="main" sx={{ flexGrow: 1, p: 3, mt: 8 }}>
          <MovieList />
        </Box>
      </Box>
    </Provider>
  );
}

export default App;
```

This implementation fetches popular movies from TMDB and displays them in a grid. You can expand on this by adding pagination, implementing the category and genre filters, and improving the UI.

Would you like me to explain any part of this implementation in more detail?
