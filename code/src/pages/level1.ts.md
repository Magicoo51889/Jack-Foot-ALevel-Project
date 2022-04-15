# level1.ts

```typescript
//importing libraries
import Phaser from "phaser";

//importing components
import { handleUsersInput, interactionKeyPressed, pauseKeyPressed, backKeyPressed } from "../../components/controls"

let platforms;
// let player;

let restart;
let ready; 

// fixed values
/*
const FUEL_MAX = 100; // Mass of fuel in tons
const SPEED = 0; // Start speed when spawn
const DRAG = 0.4; // Drag on rocket (drag coefficient is fixed)
const ROCKET_GAS_SPEED = 3000; // Velocity of exhaust gas out of engine in ms^-1
const DRY_MASS = 150; // Mass in tons
const THRUST = 2.3; // Thrust in Mega-Newtons
const EARTH_GRAVITY = 9.81; // Earth gravity in ms^-2
const AIR_DENSITY = 1.225; // Air density in kg/m^3
const VACCUM_DENSITY = 0; // Vacuum density in kg/m^3
const CROSS_SEC_AREA = 20; // Cross sectional area in m^2 based on 5m diamerter rocket

// calculated values
// const HEIGHT = player.y - platforms.y; // height above ground in m  // Need to find how to get distance from object
const TERMINAL_VELOCITY = Math.sqrt((2 * EARTH_GRAVITY * DRY_MASS)/(AIR_DENSITY||VACCUM_DENSITY * DRAG * CROSS_SEC_AREA)); // Terminal velocity in m/s^-1
const FUEL_CONSUMPTION = 0.5 * DRY_MASS * SPEED^2;  // Basic fuel consumption based off of kinetic energy used
const FUEL = FUEL_MAX - FUEL_CONSUMPTION; // Fuel in kg
const LADENED_MASS = DRY_MASS + FUEL_MAX; // Initial mass of rocket with fuel
const CURRENT_LADENED_MASS = DRY_MASS + FUEL; // Mass in kg
const ACCELERATION = THRUST - EARTH_GRAVITY; // Acceleration of rocket (arbitrary)
const SPECIFIC_IMPULSE_SEA_LEVEL = THRUST / ROCKET_GAS_SPEED * EARTH_GRAVITY;  // The impulse produced by the engine from a unit mass of propellant
const DELTA_V = SPECIFIC_IMPULSE_SEA_LEVEL * Math.log(CURRENT_LADENED_MASS / LADENED_MASS); // The distance covered in terms of the propellant required and the change in velcoity
// const ESCAPE_V = Math.sqrt((2 * EARTH_GRAVITY * CURRENT_LADENED_MASS) / HEIGHT);
*/

export default class level1 extends Phaser.Scene {

  constructor() {
    super("level1");
  }


  // main functions
  preload() {
   // this.load.image("player", "./assets/anaconda.png");
    this.load.image('ground', "./assets/platform.png");
    this.load.image('sky', "./assets/sky.png");

  }

  create() {

    this.add.image(400, 300, "sky");
    this.add.image(400, 300, "player");

    platforms = this.physics.add.staticGroup(); // static groups interact with dynamic, but CANNOT move
    // player = this.physics.add.sprite(100, 450, "player"); // dynamic groups interact with dynamic, but CAN move

    platforms.create(400, 568, 'ground').setScale(2).refreshBody();

    platforms.create(0, 250, 'ground');
    platforms.create(400, 250, 'ground');
    platforms.create(800, 250, 'ground');

  }

  /*update() {
    // player.setVelocityX(0);
    // player.setVelocityY(0);

  }*/
}

```
