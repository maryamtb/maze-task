<template>
  <div class="title">
    <h1>Random Maze Solution Generator</h1>
    <button @click="solveMaze(startPoint, endPoint)">Generate Maze</button> 

    <h3>width: {{width[0]}}, height: {{height[0]}}, startPoint: {{startPoint}} , endPoint: {{endPoint}}</h3>
      {{startPoint}}
      <div class="maze">
        <table>
            <tr><td>{{ maze[0][0] }}</td><td>{{ maze[0][1] }}</td><td>{{ maze[0][2] }}</td><td>{{ maze[0][3] }}</td></tr>
            <tr><td>{{ maze[1][0] }}</td><td>{{ maze[1][1] }}</td><td>{{ maze[1][2] }}</td><td>{{ maze[1][3] }}</td></tr>
            <tr><td>{{ maze[2][0] }}</td><td>{{ maze[2][1] }}</td><td>{{ maze[2][2] }}</td><td>{{ maze[2][3] }}</td></tr>
            <tr><td>{{ maze[3][0] }}</td><td>{{ maze[3][1] }}</td><td>{{ maze[3][2] }}</td><td>{{ maze[3][3] }}</td></tr>
        </table>
      </div>
  </div>
</template>

<script>


export default {
  name: 'Maze',
  data: function() {
    return {
      width: [4],
      height: [4],
      // size: [4].concat([4]),
      maze: [
        [0,2,0,0],
        [0,0,0,0],
        [0,0,0,0],
        [0,0,0,2]
      ],
      // maze: [
      //   ['free','blocked','blocked','blocked'],
      //   ['free','free','blocked','free'],
      //   ['blocked','free','blocked','blocked'],
      //   ['free','free','free','blocked']
      // ],
      // movingPoint: [
      //   [],[]
      // ],
      startPoint: 
        [[0,0]]
      ,
      endPoint: 
        [[3,3]]
      ,
      // movingPointList: [
      //   [],[],
      //   ]
    }
  },
  methods: {


    movePoint(startPoint) {

      let _this = this;

      // 1. check adjacent value by calling getNeighbor()
      // 2. set this.movingPoint = 'free' location (from getNeighbor())
      // 3. call solveMaze() again
      // 4. once above is complete, create stackList() => lists all moved position into a 2d array + drawLine() => sets background color for that list to red
      // if (this.movingPoint < this.width && this.movingPoint < this.height) {

      _this.getNeighbor(startPoint)
    
    },

    getNeighbor(startPoint) {
        // let _this = this;

      var i = 0
      var j = 0
      var width = this.width
      var height = this.height 

      var maze = this.maze
      let right = maze[i][j+1]
      // var down = maze[i][j+1]
      // var left = maze[i][j-1]
      // var up = maze[i-1][j]


      for (i=0; i < width-1; i++) { 
        for (j=0; j < height-1; j++) {
          if (right === 0 && right < maze[i].length-1 && maze[j].length-1) {
            startPoint = startPoint.push([i,j+1])
            console.log('pushed')
            startPoint = startPoint[0]
            return startPoint

          } else if (right === 2) {
            return startPoint
            // console.log(startPoint)
          } else {

            // console.log('something else')
          }
        }
          // return _this.solveMaze(startPoint, this.endPoint)
      }

    },

    arraysEqual([a], [b]) {
      if (a === b) return true;
      if (a === '' || b === '' || a === null || b === null) return false;
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
          if (_this.arraysEqual([startPoint], [endPoint])) {
            console.log('maze solved');
            break;
          } else {
            _this.movePoint(startPoint);
            // console.log(startPoint)
            console.log('move()')
            break;
          }
          // return this.movingPoint
        }
      }
    },

    // generateMaze(height, width, startPoint, endPoint) {
    //   height = this.height,
    //   width = this.width,
    //   startPoint = this.startPoint,
    //   endPoint = this.endPoint
    // }

  }
}
</script>

<style>

.maze {
  margin-top: 80px;
  text-align: center;
  align-items: center;
}
table, td, th {
  align-items: center;
  padding: 20px 20px;
  border: 1px solid black;
}

table {
  border-collapse: collapse;
  justify-content: center;
  margin-left:auto; 
  margin-right:auto;
}



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
