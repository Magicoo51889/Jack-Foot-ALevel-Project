# 2.2.5 Cycle 5

## Design <a href="#design" id="design"></a>

### Objectives

In this cycle I am to be able to add the weapons to the player, which interact with the enemy when they colide and then this causes an animation for the enemy to explode. This should be relatively simple to implement, as I have the enemy and the player already made, so I just need to add the functionality to them in the main scene.&#x20;

* [ ] Add lasers to the player
* [ ] Lasers can be shot using a key
* [ ] Animation when the enemy explodes

### Usability Features <a href="#usability-features" id="usability-features"></a>

### Key Variables <a href="#key-variables" id="key-variables"></a>

| Variable Name | Use                                                                                                                                                                                                                |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| lasers        | This will be the group of the lasers in the game. Using group is great for similar objects or sprites, as it reduces the load on the game as it only loads the image once, rather than for each individual laser.  |
|               |                                                                                                                                                                                                                    |

### Pseudocode <a href="#pseudocode" id="pseudocode"></a>

```
procedure lasers
    create lasers group (laser texture)
    create multiple from lasers group (10)
    enable lasers
end procedure
```

## Development <a href="#development" id="development"></a>

### Outcome <a href="#outcome" id="outcome"></a>

{% tabs %}
{% tab title="enemy.ts" %}
{% code title="enemy.ts" %}
```typescript
...
    lasers(lasers_texture:string){
        lasers = this.scene.add.group();
	lasers.enableBody = true;
	lasers.createMultiple(10, player_lasers_texture);
    }
...
```
{% endcode %}
{% endtab %}

{% tab title="Second Tab" %}
```typescript
// Some code
```
{% endtab %}
{% endtabs %}

### Challenges <a href="#challenges" id="challenges"></a>

My biggest challenge was

## Testing <a href="#testing" id="testing"></a>

Evidence for testing

### Tests <a href="#tests" id="tests"></a>

|   |   |   |
| - | - | - |
|   |   |   |
|   |   |   |
|   |   |   |

### Evidence <a href="#evidence" id="evidence"></a>
