# index.tsx

```tsx
//importing libraries
import React from 'react'
import ReactDOM from 'react-dom'

//importing pages
import App from './App'
import Game1 from './game1'

//the css used on the webpage
import "./index.css"

//Rendering the game to the webpage
ReactDOM.render(
  <div><App /><Game1/></div>,
  document.getElementById('root')
)
```
