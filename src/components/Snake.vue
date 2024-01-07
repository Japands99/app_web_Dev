<template>
  <div>
    <div v-for="row in gridSize" :key="row" class="row">
      <div v-for="col in gridSize" :key="col" class="cell" :class="{ 'snake': isSnakeCell(col, row), 'food': isFoodCell(col, row) }"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      gridSize: 20,
      snake: [{ x: 10, y: 10 }],
      food: { x: 15, y: 15 },
      direction: 'right',
      intervalId: null,
    };
  },
  mounted() {
    this.startGame();
    window.addEventListener('keydown', this.handleKeyPress);
  },
  methods: {
    startGame() {
      this.intervalId = setInterval(this.moveSnake, 200);
    },
    stopGame() {
      clearInterval(this.intervalId);
    },
    moveSnake() {
      const head = { ...this.snake[0] };

      switch (this.direction) {
        case 'up':
          head.y -= 1;
          break;
        case 'down':
          head.y += 1;
          break;
        case 'left':
          head.x -= 1;
          break;
        case 'right':
          head.x += 1;
          break;
      }

      this.checkCollision(head);
      this.snake.unshift(head);

      if (head.x === this.food.x && head.y === this.food.y) {
        this.generateFood();
      } else {
        this.snake.pop();
      }
    },
    checkCollision(head) {
      if (
        head.x < 0 || head.x >= this.gridSize ||
        head.y < 0 || head.y >= this.gridSize ||
        this.snake.some(segment => segment.x === head.x && segment.y === head.y)
      ) {
        alert('Game Over!');
        this.stopGame();
        this.resetGame();
      }
    },
    generateFood() {
      this.food = {
        x: Math.floor(Math.random() * this.gridSize),
        y: Math.floor(Math.random() * this.gridSize),
      };
    },
    handleKeyPress(event) {
      switch (event.key) {
        case 'ArrowUp':
          this.direction = 'up';
          break;
        case 'ArrowDown':
          this.direction = 'down';
          break;
        case 'ArrowLeft':
          this.direction = 'left';
          break;
        case 'ArrowRight':
          this.direction = 'right';
          break;
      }
    },
    resetGame() {
      this.snake = [{ x: 10, y: 10 }];
      this.food = { x: 15, y: 15 };
      this.direction = 'right';
    },
    isSnakeCell(x, y) {
      return this.snake.some(segment => segment.x === x - 1 && segment.y === y - 1);
    },
    isFoodCell(x, y) {
      return this.food.x === x - 1 && this.food.y === y - 1;
    },
  },
};
</script>

<style scoped>
.row {
  display: flex;
}

.cell {
  width: 20px;
  height: 20px;
  border: 1px solid #ccc;
}

.snake {
  background-color: #333;
}

.food {
  background-color: #f00;
}
</style>
