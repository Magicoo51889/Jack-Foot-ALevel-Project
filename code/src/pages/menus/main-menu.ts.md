---
description: Incomplete
---

# main-menu.ts

```typescript
//importing libraries
import Phaser from "phaser";

//importing components
import { createNewButton } from "../../components/components";

export default class MainMenu extends Phaser.Scene {
    constructor(){
        super({
            key: "MainMenu"
        })
    }

    preload(){ //import ui elements

    }

    create(){ //create ui elements

    }

    update(){ //update ui elements if pressed
        
    } 
}

function continueGame(game: { scene: { start: (arg0: string) => void; }; }){
    game.scene.start("Level1")
}e
```
