## Managing Program States aka (Switch Cycles)

### Basic Switch Format
Lets look at the following code: 

![1](https://imgur.com/MLSmKi4.png)

When the button is clciked we are switching the value of `colorChange` which is serving as our *flag* variable. A flag variable is something that monitors for states of change in our program. After the button is clicked we call the function `checkSwitchStatus` which will change the color of the text depending on the value of our flag variable. 

### Refactoring

This however can be written more succinctly as

![2](https://imgur.com/ACbCTuN.png)

`changeColor = !changeColor` all this does is continously flip it to its `inverse value`. From `false` to `true` from `true` to `false` so on so forth infinitly. 

Next lets inline our `checkSwitchStatus` function

![3](https://imgur.com/gg4Dt52.png)

### Another Option

These next two options use closure. We can employ closure to make `changeState` local to the event handler:

![3](https://imgur.com/IsAiqQb.png)

This portion of the code is an anonymous self executing function

![3.5](https://imgur.com/VC3d1Oy.png)

### And another Option

![4](https://imgur.com/ETzGoWY.png)

