<template>
  <div class="title">
    <h1>Random Maze Solution Generator</h1>
    <button @click="solveMaze(startPoint, endPoint)">Generate Maze</button> 

    <h3>width: {{width[0]}}, height: {{height[0]}}, startPoint: {{startPoint}} , endPoint: {{endPoint}}</h3>
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
        ['free','free','free','blocked']
      ],
      movingPoint: [
        [],[]
      ],
      startPoint: [
        [0],[0]
      ],
      endPoint: [
        [3],[3]
      ],
      movingPointList: [
        [],[],
        ]
    }
  },
  methods: {

    getNeighbor() {
      let _this = this;

      var i = 0
      var j = 0
      if (this.maze[i][j+1] === 'blocked' && this.maze[i]-1 < this.width && this.maze[j]-1 < this.height) { 
        this.movingPoint = [i+1,j]

        // this.movingPointList.push([this.movingPoint[0]],[this.movingPoint[1]])
        // console.log(this.movingPointList)

        return _this.solveMaze( [ this.movingPoint = [i+1,j] ] , [this.endPoint])
        // return _this.solveMaze( [ [this.movingPoint[0]],[this.movingPoint[1]] ]  , [this.endPoint])

      } else if (this.maze[i+1][j] === 'free' && this.maze[i]-1 < this.width && this.maze[j]-1 < this.height) { 
        this.movingPoint = [i,j+1]
        // this.movingPointList.push([this.movingPoint[0]],[this.movingPoint[1]])
        
        return _this.solveMaze( this.movingPoint[i,j+1] , [this.endPoint])
        // _this.solveMaze( [ [this.movingPoint[0]],[this.movingPoint[1]] ]  , [this.endPoint])

      } else if (this.maze[i]-1 === this.width && this.maze[i-1][j] === 'free') {
        this.movingPoint = [i-1,j]
        // this.movingPointList.push([this.movingPoint[0]],[this.movingPoint[1]])

        console.log('out of range x-axis')
        return _this.solveMaze( this.movingPoint = [i-1,j] , [this.endPoint])
        // return _this.solveMaze( [ [this.movingPoint[0]],[this.movingPoint[1]] ]  , [this.endPoint])

      } else if (this.maze[i]-1 === this.height && this.maze[i][j-1] === 'free') {
        this.movingPoint = [i,j-1]
        // this.movingPointList.push([this.movingPoint[0]],[this.movingPoint[1]])
        console.log('out of range y-axis')
        
        return _this.solveMaze( this.movingPoint = [i,j-1] , [this.endPoint])
        // return _this.solveMaze( [ [this.movingPoint[0]],[this.movingPoint[1]] ]  , [this.endPoint])
      } else if (this.maze[i][j] === this.movingPoint[i][j]) {
        // console.log([this.movingPoint], [this.endPoint])
        console.log('winner')
        // _this.solveMaze( movingPoint  , [this.endPoint])
      } else {
          
          // return _this.solveMaze({ startPoint: [ [this.movingPoint[0]],[this.movingPoint[1]] ] } , { endPoint: [this.endPoint]})
          console.log('something else')
      }

    },

    movePoint() {
      // this.movingPoint = this.startPoint;
      let _this = this;
      // 0. check if on edge
      // 1. check adjacent value by calling getNeighbor()
      // 2. set this.movingPoint = 'free' location (from getNeighbor())
      // 3. call solveMaze() again
      // 4. once above is complete, create stackList() => lists all moved position into a 2d array + drawLine() => sets background color for that list to red
      
      _this.getNeighbor()


    },

    arraysEqual([a], [b]) {
      if (a === b) return true;
      if (a === '' || b === '' && a === null && b === null) return false;
      for (var i = 0; i < a.length; i++) {
        if (a[i] !== b[i]) return false;
      }
      return true;
    },

    solveMaze(startPoint, endPoint) {
      let _this = this;
      // startPoint = '';
      for (var i=0; i < this.maze.length; i++) {
        var mazeColumn = this.maze[i];
        for (var j=0; j < mazeColumn.length; j++) {
          if (_this.arraysEqual([startPoint], [endPoint])) {
            console.log('maze solved');
          } else {
            this.startPoint = startPoint

            _this.movePoint();
            console.log('move()')
          }
          return [this.movingPoint]
        }
      }
    }


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
