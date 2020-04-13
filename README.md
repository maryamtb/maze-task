# maze

## task description

Initially, the maze task was set up with a button (generate Maze) that called the solveMaze function, with a maze that had set width and height values to reduce complexity. solveMaze would loop over the maze and call movePoint() which then would create a list that reflected that movement. movePoint() navigated with 4 different cases where the point could either the move up, down, left, or right methods.

A recursive call was then implemented to the logic. solveMaze() first identified whether the startpoint and endpoints (set as 0,0 and 3,3 once again to reduce complexity) were equivalent by calling the arraysEqual() method. arraysEqual() identified whether they were or not. If the values were equal, the maze was solved, if not, solveMaze() called the movePoint() method. A simpler matrix was used in the process for writing the movePoint() method. movePoint() then called the getNeighbor() method and the movingpoint list idea was removed. Instead, once movePoint() was called with this.startPoint passed down, it would then call getNeighbor() on the switch expression for that startPoint. getNeighbor() looped over the width and height values of the matrix (still set as fixed) and then identified if the value of the maze position was either 0 or not. This logic would follow each direction. If the right value was free, for instance, then the startPoint array was pushed [i,j+1] back in the movePoint() method. movePoint() then performs a recursive call to the solveMaze() moving the "re-initialized" startpoint back to the solveMaze() in order to re-evaluate its positioning/identify the next step. (recursive call commented out as there was an infinite loop). break statement added at the end of movePoint() to reflect a cost of 1 only. The next idea was to follow the logic for directions down, up, and left and pushing the startPoint array to reflect the positioning. On a UI level, a Grid Vue component would display the matrix and change the background color for the startpoint as the array grew. The generate maze button would also have width, height, startpoint, and endpoint values that are randomnly generated instead of the given fixed ones. That button would then call the generateMaze() method which would call the solveMaze() with Math.random added to the data values.

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
