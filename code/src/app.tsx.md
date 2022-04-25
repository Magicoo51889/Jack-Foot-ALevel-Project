# App.tsx

```tsx
import Phaser from 'phaser';

import TestScene from './scenes/PlayScene';

const config:GameConfig = {
    type: Phaser.AUTO,
    parent: 'content',
    width: innerWidth,
    height: innerHeight,
    resolution: 1, 
    backgroundColor: "#EDEEC9",
    physics: {
      default: "matter",
      matter: {
        gravity: {y: 9.81},
        debug: false
      }
    },
    scene: [
      TestScene
    ]
};

new Phaser.Game(config);

```
