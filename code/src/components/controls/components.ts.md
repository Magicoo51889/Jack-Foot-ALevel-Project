# components.ts

```typescript
import Phaser from "phaser"

export function createNewKeys(game: { player1: { left: any; right: any; up: any; down: any; rotateLeft: any; rotateRight: any; interactionKey: { pressed: boolean }; back: any }; input: { keyboard: { addKey: (arg0: number) => any } }; pauseButton: any }){

    game.player1.left = game.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.A)
    game.player1.right = game.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.D)
    game.player1.up = game.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.W)
    game.player1.down = game.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.S)
    game.player1.rotateLeft = game.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.Q)
    game.player1.rotateRight = game.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.E)
    
    game.player1.interactionKey = game.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.ENTER)
    game.player1.back = game.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.BACKSPACE)
    game.player1.interactionKey.pressed = false
    game.pauseButton = game.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.ESC)
}

export function createNewButton(game: { add: { sprite: (arg0: number, arg1: number, arg2: any) => any; rectangle: (arg0: number, arg1: number, arg2: number, arg3: number, arg4: number) => any }; anims: { create: (arg0: { key: string; frames: { key: string }[] | { key: string }[]; frameRate: number }) => void } }, physicsGroup: { add: (arg0: any) => void }, info: { x: number; y: number; width: number; height: number }, scale: number, sprite: any){
    let button
    if(sprite){
        button = game.add.sprite(info.x*scale, info.y*scale-10*scale, sprite)
        button.setDisplaySize(info.width*scale, info.width*scale)
        game.anims.create({
            key: "off",
            frames: [{key: "buttonup"}],
            frameRate: 5,
        })
        game.anims.create({
            key: "on",
            frames: [{key: "buttondown"}],
            frameRate: 5,
        })
        button.animation = "off"
    }
    else{
        button = game.add.rectangle(info.x*scale, info.y*scale, info.width*scale, info.height*scale, 0xffff00)
    }
    physicsGroup.add(button)
    button.on = false
    return button
}
```
