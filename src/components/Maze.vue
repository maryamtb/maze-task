<template>
  <div class="title">
    <h1>Random Maze Solution Generator</h1>
    <button @click="solveMaze(startPoint, endPoint)">Generate Maze</button> 
  </div>
</template>

<script>

export default {
  name: 'Maze',
  data: function() {
    return {
      width: [4],
      height: [4],
      size: [4].concat([4]),
      // maze: [
      //   [1,0,0,0],
      //   [1,1,0,1],
      //   [0,1,0,0],
      //   [1,1,1,1]
      // ],
      maze: [
        ['free','blocked','blocked','blocked'],
        ['free','free','blocked','free'],
        ['blocked','free','blocked','blocked'],
        ['free','free','free','free']
      ],
      movingPoint: [
        [],[]
      ],
      startPoint: [
        [0],[0]
      ],
      endPoint: [
        [3],[3]
      ]
    }
  },
  methods: {

    getNeighbor() {
      // 1. start with right then bottom (i++ & j++), check for borders/edges (maybe create function for that) & make it only 1 step
      // 2. if free return location of the free cell
    },

    movePoint() {
      // 1. check adjacent value by calling getNeighbor()
      // 2. set this.movingPoint = 'free' location (from getNeighbor())
      // 3. call solveMaze() again
      // 4. once above is complete, create stackList() => lists all moved position into a 2d array + drawLine() => sets background color for that list to red
    },

    arraysEqual([a], [b]) {
      if (a === b) return true;

      for (var i = 0; i < a.length; i++) {
        if (a[i] !== b[i]) return false;
      }
      return true;
    },

    solveMaze(startPoint, endPoint) {
      let _this = this;
      for (var i=0; i < this.maze.length; i++) {
        var mazeColumn = this.maze[i];
        for (var j=0; j < mazeColumn.length; j++) {
          if (_this.arraysEqual(startPoint, endPoint)) {
            console.log('maze solved');
          } else {
            console.log('move()')
          }
        }
      }
    }


  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
