<template>
  <div class="title">
    <h1>Maze Task: Depth First Search</h1>
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
        [4],[4]
      ]
    }
  },
  methods: {

    movePoint() {
      let _this = this
      switch(expression) {
        case adjacentRight = 'blocked':
          _moveLeft() || _moveDown() || _moveUp()
          break;
        case adjacentDown = 'blocked':
          _moveLeft() || _moveRight() || _moveUp()
          break;
        case adjacentUp = 'blocked':
          _moveLeft() || _moveRight() || _moveDown()
          break;
        case adjacentLeft = 'blocked':
          _moveDown() || _moveRight() || _moveUp()
          break;
      default:
      }
    },

    moveDown() {
      return this.j--;
    },

    moveRight() {
      return this.i++;
    },

    moveLeft() {
      return this.i--;
    },

    moveUp() {
      return this.j--;
    },

    solveMaze(startPoint, endPoint) {
      let _this = this;

      for(var i=0; i <= 1; i++) {
        for (var j=0; j <= 1; j++) {
          if (startPoint == this.startPoint && endPoint == this.endPoint) {
            this.movingPoint = startPoint;
            _this.movePoint()

          } else if (this.movingPoint == this.endPoint) {
            console.log('Maze solved');
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
