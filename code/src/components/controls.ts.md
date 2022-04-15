# controls.ts

```typescript
// Called every frame to check if keys are pressed

export function handleUsersInput(game: any, scale: number){
    if(game.player1.left.isDown){
        game.player1.sprite.setVelocityX(-game.player1.speed * scale)
    }
    else if(game.player1.right.isDown){
        game.player1.sprite.setVelocityX(game.player1.speed * scale)
    }
    else{
        game.player1.sprite.setVelocityX(0)
    }

    if(game.player1.up.isDown){
        game.player1.sprite.setVelocityY(game.player1.speed * scale)
    }
    else if(game.player1.down.isDown){
        game.player1.sprite.setVelocityY(-game.player1.speed * scale)
    }
    else{
        game.player1.sprite.setVelocityY(0)
    }

    if (game.player1.rotateLeft.isDown){
        game.player1.sprite.setAngularVelocity(-game.player1.rotationSpeed * scale)
    }
    else if (game.player1.rotateRight.isDown){
        game.player1.sprite.setAngularVelocity(game.player1.rotationSpeed * scale)
    }
    else{
        game.player1.sprite.setAngularVelocity(0)
    }
}

export function interactionKeyPressed(game: any){
    if(game.player1.interactionKey.isDown){
        game.player1.interactionKey.pressed = true
        return true
    }
    return false
}

export function backKeyPressed(game: any){
    if(game.player1.back.isDown){
        game.player1.back.pressed = true
        return true
    }
    return false
}

export function pauseKeyPressed(game: any){
    if(game.pauseButton.isDown){
        game.pauseButton.pressed = true
        return true
    }
    return false
}
```
