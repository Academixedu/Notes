# Interactive Tutorial: Mastering Material-UI (MUI) Components

Welcome to this hands-on tutorial where we'll explore and customize Material-UI components! We'll focus on creating a responsive app bar and a permanent drawer for a movie application.

## Step 1: Setting Up

First, create a new React project and install MUI:

```bash
npx create-react-app mui-movie-app
cd mui-movie-app
npm install @mui/material @mui/icons-material @emotion/react @emotion/styled
```

## Step 2: Creating the App Bar

Let's start with the app bar. Create a file named `CustomAppBar.js`:

```jsx
import React from 'react';
import { AppBar, Toolbar, InputBase, Button, Box } from '@mui/material';
import SearchIcon from '@mui/icons-material/Search';
import AccountCircleIcon from '@mui/icons-material/AccountCircle';

function CustomAppBar() {
  return (
    <AppBar position="fixed">
      <Toolbar>
        <Box component="img" src="/logo.png" alt="Logo" sx={{ height: 40 }} />
        <Box sx={{ flexGrow: 1, display: 'flex', alignItems: 'center', ml: 2 }}>
          <SearchIcon />
          <InputBase placeholder="Search for a movie..." sx={{ ml: 1 }} />
        </Box>
        <Button color="inherit" startIcon={<AccountCircleIcon />}>
          Login
        </Button>
      </Toolbar>
    </AppBar>
  );
}

export default CustomAppBar;
```

## Step 3: Customization Playground

Now, let's make our app bar customizable. Replace the content of `CustomAppBar.js` with:

```jsx
import React from 'react';
import { AppBar, Toolbar, InputBase, Button, Box } from '@mui/material';
import SearchIcon from '@mui/icons-material/Search';
import AccountCircleIcon from '@mui/icons-material/AccountCircle';

function CustomAppBar() {
  // Experiment: Change these values
  const appBarColor = 'primary';
  const appBarElevation = 4;
  
  const logoStyle = {
    height: 40,
    marginRight: 2,
    // Experiment: Add more styles here
  };
  
  const searchBoxStyle = {
    backgroundColor: 'rgba(255, 255, 255, 0.15)',
    borderRadius: '4px',
    padding: '0 10px',
    // Experiment: Customize further
  };
  
  const loginButtonStyle = {
    // Experiment: Style the login button
  };

  return (
    <AppBar position="fixed" color={appBarColor} elevation={appBarElevation}>
      <Toolbar>
        <Box component="img" src="/logo.png" alt="Logo" sx={logoStyle} />
        <Box sx={{ flexGrow: 1, display: 'flex', alignItems: 'center', ...searchBoxStyle }}>
          <SearchIcon />
          <InputBase placeholder="Search for a movie..." sx={{ ml: 1, flexGrow: 1 }} />
        </Box>
        <Button color="inherit" startIcon={<AccountCircleIcon />} sx={loginButtonStyle}>
          Login
        </Button>
      </Toolbar>
    </AppBar>
  );
}

export default CustomAppBar;
```

## Interactive Exercises:

1. Change `appBarColor` to "secondary" or "#ff4081". What happens?
2. Adjust `appBarElevation` between 0 and 24. How does it affect the shadow?
3. In `logoStyle`, add `filter: 'invert(1)'`. How does it change the logo?
4. Modify `searchBoxStyle`:
   - Change `backgroundColor` to 'rgba(0, 0, 0, 0.2)'
   - Add `transition: 'all 0.3s'`
   - Implement a hover effect: `'&:hover': { backgroundColor: 'rgba(255, 255, 255, 0.25)' }`
5. Style `loginButtonStyle`:
   - Add `borderRadius: '20px'`
   - Set `textTransform: 'none'`
   - Implement a hover effect

## Step 4: Creating the Drawer

Now, let's create a permanent drawer. Create a file named `CustomDrawer.js`:

```jsx
import React from 'react';
import { Drawer, List, ListItem, ListItemIcon, ListItemText, Typography, Divider, Box } from '@mui/material';
import MovieIcon from '@mui/icons-material/Movie';
import StarIcon from '@mui/icons-material/Star';
import UpcomingIcon from '@mui/icons-material/Upcoming';

const drawerWidth = 240;

const categories = [
  { name: 'Popular', icon: <MovieIcon /> },
  { name: 'Top Rated', icon: <StarIcon /> },
  { name: 'Upcoming', icon: <UpcomingIcon /> },
];

function CustomDrawer() {
  // Experiment: Customize these styles
  const drawerStyle = {
    width: drawerWidth,
    flexShrink: 0,
    '& .MuiDrawer-paper': {
      width: drawerWidth,
      boxSizing: 'border-box',
      backgroundColor: '#0d253f',
      color: '#01b4e4',
    },
  };

  const listItemStyle = {
    '&:hover': {
      backgroundColor: '#01b4e4',
      '& .MuiListItemIcon-root, & .MuiTypography-root': {
        color: '#ffffff',
      },
    },
  };

  return (
    <Drawer sx={drawerStyle} variant="permanent" anchor="left">
      <Box sx={{ overflow: 'auto', mt: 8 }}>
        <Typography variant="h6" sx={{ px: 2, py: 1 }}>
          Categories
        </Typography>
        <List>
          {categories.map((item) => (
            <ListItem key={item.name} disablePadding>
              <ListItemIcon sx={{ color: 'inherit' }}>{item.icon}</ListItemIcon>
              <ListItemText primary={item.name} />
            </ListItem>
          ))}
        </List>
      </Box>
    </Drawer>
  );
}

export default CustomDrawer;
```

## Interactive Exercises:

1. Change the `drawerWidth`. How does it affect the layout?
2. Modify the drawer's background color and text color.
3. Add a hover effect to list items by implementing the `listItemStyle`.
4. Add more categories to the `categories` array with different icons.
5. Implement a divider between categories using the `Divider` component.

## Step 5: Putting It All Together

In your `App.js`, combine the AppBar and Drawer:

```jsx
import React from 'react';
import { Box } from '@mui/material';
import CustomAppBar from './CustomAppBar';
import CustomDrawer from './CustomDrawer';

function App() {
  return (
    <Box sx={{ display: 'flex' }}>
      <CustomAppBar />
      <CustomDrawer />
      <Box component="main" sx={{ flexGrow: 1, p: 3, mt: 8, ml: 30 }}>
        {/* Main content goes here */}
        <h1>Welcome to Movie App!</h1>
      </Box>
    </Box>
  );
}

export default App;
```

## Final Challenge:

1. Make the app responsive:
   - Hide the drawer on small screens
   - Add a menu icon to the AppBar that shows/hides the drawer on small screens
2. Implement a dark mode toggle in the AppBar
3. Add animations to the drawer opening/closing

Remember, the key to mastering MUI is experimentation. Don't be afraid to try extreme values or combinations – it's the best way to understand how components behave and interact!
