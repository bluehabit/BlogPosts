## Managing Program States aka (Switch Cycles)

Lets look at the following code: 

![1](https://imgur.com/MLSmKi4.png)

When the button is clciked we are switching the value of `colorChange` which is serving as our *flag* variable. A flag variable is something that monitors for states of change in our program. After the button is clicked we call the function `checkSwitchStatus` which will change the color of the text depending on the value of our flag variable. 

This however can be written more succinctly as

![2](https://imgur.com/ACbCTuN.png)

`changeColor = !changeColor` all this does is continously flip it to its inverse value. From `false` to `true` from `true` to `false` so on so forth infinitly. 
