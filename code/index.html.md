# index.html

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Phaser - ES6 - Webpack</title>
    <meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no">
    <meta name="HandheldFriendly" content="True">
    <meta name="MobileOptimized" content="320">
    <meta http-equiv="cleartype" content="on">
    <meta name="format-detection" content="telephone=no">
    <meta name="theme-color" content="#ffffff">
    <link rel="manifest" href="/manifest.json">
    <style>
        html,
        body {
            font: 16px Arial, Helvetica, sans-serif;
            margin: -0.10%;
        }

        #game-wrapper {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
            background: blue;
            width: 400px;
            height: 730px;
            position: relative;
            border: 5px solid white;
        }
         header{
             display: none;
        }
         footer{
           display: none;
        }
        .score{
             position: absolute;
             color: white;
             bottom: 90%;
             font-family: 'Press Start 2P';
        }
        .title{
             position: absolute;
             color: yellow;
             height: fit-content;
             padding: 5px;
             top: 20%;
             bottom: 80%;
             left: 116%;
             width: max-content;
             font-family: 'Press Start 2P';
        }
        .gameover{
           position: absolute;
           color: red;
           bottom: 50%;
           font-family: 'Press Start 2P';
           display: none;
        }
        .restart{
           position: absolute;
           color: white;
           bottom: 50%;
           font-family: 'Press Start 2P';
           cursor: pointer;
           border: 2px solid white;
           padding: 5px;
           margin-bottom: -5%;
        }
        .restart:hover{
           color: yellow;
        }
        #health{
           position: absolute;
           color: white;
           bottom: 1%;
           font-family: 'Press Start 2P';
        }
        .display-none{
           display: none;
        }
        .glowText{
           animation-name: glow;
           animation-duration: 1s;
        
        }
        .highscore-div{
                position: absolute;
                padding-left: 3%;
                bottom: 5%;
            }
        .highscore{
            color: white;
            font-family: 'Press Start 2P';
            width: 100%;
            line-height: 1.2em;
        }
        .instructions{
            position: absolute;
            color: white;
            height: fit-content;
            padding: 5px;
            bottom: 50%;
            font-family: 'Press Start 2P';
            line-height: 1.2em;
            top: 40%;
            left: 122%;
            width: 75%;
            text-align: center;
        }
        @keyframes glow {
           from {color: white;}
           to {color: yellow;}
         }
        @media only screen and (min-width: 768px){
            .desktop-margins{
                background: black;

            }
            header{
                padding-top: 10px;
                display: inherit;
                text-align: center;
                background: black;
                height: 75px;
                width: 100%;
                color: white;
                font-family: 'Press Start 2P';
                font-size: 20px;
            }
            footer{
                padding-top: 35px;
                display: inherit;
                text-align: center;
                background: black;
                height: 75px;
                width: 50%;
                line-height: 1.5em;
                color: white;
                font-family: 'Press Start 2P';
                font-size: 20px;
            }
            .outside-game{
              margin: auto;
              position: absolute;
              padding-left: 10%;
              width: 90%;
              background: black;
            }
            .character-image{
                position: absolute;
                right: 57%;
                margin-top: 8%;
                height: 300px;
                width: 200px;
                border: 2px solid white;
                background-image: url('assets/commanderplaceholder.png');
                background-size: cover;;
            }
            .character-text{
                display: initial; 
                position: absolute;
                width: 110%;
                top: 300px;
                color: white;
                font-family: 'Press Start 2P';
                line-height: 1.5em;
            }
            
        
            .player-image{
                position: absolute;
                left: 80%;
                margin-top: 8%;
                height: 300px;
                width: 200px;
                border: 2px solid white;
                background-image: url('assets/placeholderdog.png');
                background-size: cover;
            }
            .saturate{
                filter: saturate(6000%);

            }
            .player-text{
                display: initial; 
                position: absolute;
                width: 110%;
                top: 300px;
                color: white;
                font-family: 'Press Start 2P';
                line-height: 1.5em;
            }
        }

    </style>
</head>

<body>
    <div class="outside-game">    
        <div id="game-wrapper">
                <h1 class="score">Score: 0</h1>
                <h1 class="gameover">GAME OVER</h1>
                <div class="restart display-none">RESTART</div>
                <h4 id="health">Health: 200
                <h1 class="title"> Escape the enemy hoard!
                <h3 class="instructions">Use the arrow keys to move side to side. You shoot when you move! <br>  <br> To score either shoot the enemies or pick up health. Good luck!</h3>
                <div class="highscore-div">
                    <h1 class="highscore">High Score: </h1>
                </div>
        </h1></h4></div>
        
        <div class="game"></div>
        <footer>Created by Jack Foot</footer>
    </div>
    
<div id="content"></div>
    <script type="text/javascript" src="cordova.js"></script>
<script type="text/javascript" src="./dist/vendor.bundle.js"></script><script type="text/javascript" src="./dist/bundle.js"></script></body>

</html>
```
