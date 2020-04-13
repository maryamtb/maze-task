<template>
  <div class="title">
    <h1>Random Maze Solution Generator</h1>
    <button @click="solveMaze(startPoint, endPoint)">Generate Maze</button> 

    <h3>width: {{width[0]}}, height: {{height[0]}}, startPoint: {{startPoint}} , endPoint: {{endPoint}}</h3>

      <div class="maze">

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
        [0,1,1,1],
        [0,0,1,0],
        [1,0,1,1],
        [0,0,0,1]
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
      var i = 0 
      var j = 0
      let right = this.maze[i][j+1]
      let down = this.maze[i+1][j]


      // 1. check adjacent value by calling getNeighbor()
      // 2. set this.movingPoint = 'free' location (from getNeighbor())
      // 3. call solveMaze() again
      // 4. once above is complete, create stackList() => lists all moved position into a 2d array + drawLine() => sets background color for that list to red


      switch (_this.getNeighbor(startPoint)) {
        case right:
          startPoint = startPoint.push([i,j+1])

          console.log(startPoint)
          // _this.solveMaze(startPoint, this.endPoint)
          break;
        case down:
          this.startPoint = startPoint.push([i+1,j])
          console.log(this.startPoint)
          // _this.solveMaze(startPoint, this.endPoint)
          break;
      //   case left: 
      //     _this.getNeighbor(startPoint)
      //     break;
      //   case up: 
      //     _this.getNeighbor(startPoint)
      //     break;
        default:
          //  _this.solveMaze(startPoint, this.endPoint)
          // console.log(startPoint)
          break;
      // }
      }
    },

    getNeighbor() {
      // let _this = this;
      var i = 0
      var j = 0
      var width = this.width
      var height = this.height 

      var maze = this.maze
      let right = maze[i][j+1]
      let down = maze[i+1][j]
      // var left = maze[i][j-1]
      // var up = maze[i-1][j]
      // var right = [maze[i][j], maze[i][j]+1]
      // var down = [maze[i][j]+1, maze[i][j]]

      // console.log([maze[i][j], maze[i][j]+1])
      // console.log([maze[i][j]+1, maze[i][j]])

      for (var a=0; a < width-1; a++) { 
        for (var b=0; b < height-1;b++) {
          if (right === 0 || down === 0 && right || down < maze[i].length-1 && right || down < maze[j].length-1) {
            return right, down
            // console.log('r we here')
          } else {
            console.log('something else')
          }
        }
        break;
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

          } else {
            _this.movePoint(startPoint);

            console.log('move()')

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
