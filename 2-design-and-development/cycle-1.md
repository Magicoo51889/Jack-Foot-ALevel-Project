# 2.2.1 Cycle 1 - Creating Game

## Design

### Objectives

In this cycle my aim was to create my basic HTML5 webpage using JavaScript.

I used a boilerplate to be able to get the file structure I need, and this boilerplate also had webpack and ES6 preconfigured. Additonally it allows for the program to run on mobile devices easily using Apache Cordova, which natively runs apps on iOS and Android.

&#x20;I then installed Phaser.js which is the game engine library that I will be using, which provides a physics engine and it also is efficient at drawing and receiving inputs from the user using functions.

I opted to go with the older version of Phaser being Phaser 2 as the newer Phaser 3, as some people in the community have said that it can be difficult to find documentation and reliable sources of code for the newer version. This is mainly due to the newer version being out for much less time than the older version has been. The older version has also been dubbed as the community edition as it is open for the community to fix and patch the framework and is the recommended framework to use till Phaser 3 becomes adopted.

* [x] Get website to load and work on localhost:3000
* [x] Getting the page to fit the screen

### Usability Features

### Key Variables

| Variable Name | Use                                                                                                |
| ------------- | -------------------------------------------------------------------------------------------------- |
| player        | This is the variable that stores the properties of the spaceship sprite.                           |
| preload       | This is the function that loads all assets into the scene.                                         |
| update        | This function is the function that updates each frame to update the position of the sprite.        |
| create        | This function is called at the start of the game to initialise all the variables and sprites etc.  |

### Pseudocode

```
procedure create
    load map
    load player
end procedure
```

## Development

### Outcome

The Game.js file is where the game is and it is where the different planets will be added later on, and is where I have setup the controls from my components folder and added it to the update function so that they update each frame. I've also made it so that the program is coded chronologically, and this means that debugging is easier as I know that the most essential core parts of the program will be earlier on in the application's code, and I've also made sure to comment everything so that I know what parts do what, also aiding future debugging, and for anyone else who may look at the code.&#x20;

I've also used functions for each different part of the program as this modularises the program up into different smaller chunks, and makes it easier to debug. It is also a modern programming practise that should be followed everywhere possible as it  makes the code neater and improves the performace of the program.&#x20;

{% tabs %}
{% tab title="PlayScene.ts" %}
{% code title="playScene.ts" %}
```javascript
// Create game

const game = new Phaser.Game(400, 730, Phaser.AUTO, 'game-wrapper', {
  preload: preload,
  create: create,
  update: update,
});

let player;
let background;
let health = 200;

// Loads all assets
function preload() {
  // Load all assets
  game.load.image('background', 'assets/images/spacebg.gif');
  // Player ship
  game.load.image('playerShip', 'assets/images/playerShip.gif');
}

// This function holds all the game logic

function create() {
  game.physics.startSystem(Phaser.Physics.ARCADE); // Add physics engine

  background = game.add.tileSprite(0, 0, 1000, 600, 'background');
  background.scale.x = 1;
  background.scale.y = 2;
 
  // Set player to playerShip
  // Set player to game.add.sprite to enable body physics
  player = game.add.sprite(game.canvas.width / 2, game.canvas.height - 100, 'playerShip');
  player.scale.set(0.9); // Scales the player's image smaller
  game.physics.arcade.enable(player, Phaser.Physics.ARCADE); // Set player physics
  player.anchor.set(0.5, 1); // Position player's anchor point to the middle of sprite
  player.x = game.input.x || game.world.width * 0.5; // Player starts in middle of screen
  player.body.velocity.x = 200; // Set default x velocity to 200
}

```
{% endcode %}
{% endtab %}

{% tab title="Main.ts" %}
{% code title="main.ts" %}
```typescript
import 'pixi'
import 'p2'
import Phaser from 'phaser'

import BootState from './states/Boot'
import SplashState from './states/Splash'
import GameState from './states/Game'

import config from './config'

class Game extends Phaser.Game {
  constructor () {
    const docElement = document.documentElement
    const width = docElement.clientWidth > config.gameWidth ? config.gameWidth : docElement.clientWidth
    const height = docElement.clientHeight > config.gameHeight ? config.gameHeight : docElement.clientHeight

    super(width, height, Phaser.CANVAS, 'content', null)

    this.state.add('Boot', BootState, false)
    this.state.add('Splash', SplashState, false)
    this.state.add('Game', GameState, false)

    // with Cordova with need to wait that the device is ready so we will call the Boot state in another file
    if (!window.cordova) {
      this.state.start('Boot')
    }
  }
}

window.game = new Game()

if (window.cordova) {
  var app = {
    initialize: function () {
      document.addEventListener(
        'deviceready',
        this.onDeviceReady.bind(this),
        false
      )
    },

    // deviceready Event Handler
    //
    onDeviceReady: function () {
      this.receivedEvent('deviceready')

      // When the device is ready, start Phaser Boot state.
      window.game.state.start('Boot')
    },

    receivedEvent: function (id) {
      console.log('Received Event: ' + id)
    }
  }

  app.initialize()
}

if ('serviceWorker' in navigator) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('/service-worker.js').then(registration => {
      console.log('SW registered: ', registration)
    }).catch(registrationError => {
      console.log('SW registration failed: ', registrationError)
    })
  })
}

```
{% endcode %}
{% endtab %}

{% tab title="Index.html" %}
{% code title="index.html" %}
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Phaser3 - ES6 - Webpack</title>
    <meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no">
    <meta name="HandheldFriendly" content="True">
    <meta name="MobileOptimized" content="320">
    <meta http-equiv="cleartype" content="on">
    <meta name="format-detection" content="telephone=no">
    <style>
        html,
        body {
            margin: 0;
            padding: 0;
        }
    </style>
</head>

<body>
    <div id="content"></div>
<script type="text/javascript" src="./dist/vendor.bundle.js"></script><script type="text/javascript" src="./dist/bundle.js"></script></body>
</html>
```
{% endcode %}
{% endtab %}
{% endtabs %}

Using the package.json you are able to install all libraries and modules, by running **`npm install`**, and then you can run it by **`npm run dev`**. This will use webpack to deploy the webpage to localhost//:3000, where I am able to develop the game, and then when I want to fully bundle the game I can run the command **`npm run deploy`** as this will fully package the game, and make it a smaller file size so that it loads faster and is less demanding on the computer.

### Challenges

As this was simply setting up Phaser and Webpack it wasn't particularly difficult as there's lots of tutorials on how to install both, and I used a boilerplate to make it even easier as it was all preconfigured and working before hand. My only issue was:

* Adding the player to the screen

## Testing

Evidence for testing

### Tests

<table><thead><tr><th>Test</th><th>Instructions</th><th>What I expect</th><th>What actually happens</th><th data-type="select">Pass/Fail</th></tr></thead><tbody><tr><td>1</td><td>Run code</td><td>Page to load and be rendered to fit the screen.</td><td>Page loads after compiling and all renders, whilst fitting to screen.</td><td></td></tr><tr><td>2</td><td>Press arrow keys</td><td>Arrow keys allow basic movement of sprite on page.</td><td>The sprite moves side to side.</td><td></td></tr><tr><td>3</td><td>Press A D Keys</td><td>Player moves side to side with each press of the key.</td><td>The sprite moves side to side.</td><td></td></tr></tbody></table>

### Evidence

In this game I'm able to use the arrow keys to move around, and the sprite points in the direction of travel.&#x20;

<figure><img src="../.gitbook/assets/image (3) (3).png" alt=""><figcaption><p>The player ship in the game</p></figcaption></figure>

### What next?

* I'd like to add the ability to control the player's ship
