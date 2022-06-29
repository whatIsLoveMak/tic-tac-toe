<template>
  <div class="app">
    {{ endGame }}
    <div class="grid">
      <div
        @click="clickPlayer(item)"
        v-for="item in gridItems"
        :key="item.id"
        class="grid-item"
      >
        <div>{{ item.value }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      player: true,
      gridItems: [
        {
          id: 1,
          value: '',
        },
        {
          id: 2,
          value: '',
        },
        {
          id: 3,
          value: '',
        },
        {
          id: 4,
          value: '',
        },
        {
          id: 5,
          value: '',
        },
        {
          id: 6,
          value: '',
        },
        {
          id: 7,
          value: '',
        },
        {
          id: 8,
          value: '',
        },
        {
          id: 9,
          value: '',
        },
      ],
      row1: [],
    }
  },
  methods: {
    clickPlayer(item) {
      if (item.value === '') {
        this.player ? (item.value = 'x') : (item.value = '0')
        this.player = !this.player
      }
    },
  },
  computed: {
    endGame() {
      let filteredArr = this.gridItems.filter((elem) => elem.value !== '')
      if (
        this.gridItems[0].value === 'x' &&
        this.gridItems[1].value === 'x' &&
        this.gridItems[2].value === 'x'
      ) {
        return alert('player 1 won')
      } else if (
        this.gridItems[0].value === '0' &&
        this.gridItems[1].value === '0' &&
        this.gridItems[2].value === '0'
      ) {
        return alert('player 2 won')
      } else if (
        this.gridItems[3].value === 'x' &&
        this.gridItems[4].value === 'x' &&
        this.gridItems[5].value === 'x'
      ) {
        return alert('player 1 won')
      } else if (
        this.gridItems[3].value === '0' &&
        this.gridItems[4].value === '0' &&
        this.gridItems[5].value === '0'
      ) {
        return alert('player 2 won')
      } else if (
        this.gridItems[6].value === 'x' &&
        this.gridItems[7].value === 'x' &&
        this.gridItems[8].value === 'x'
      ) {
        return alert('player 1 won')
      } else if (
        this.gridItems[6].value === '0' &&
        this.gridItems[7].value === '0' &&
        this.gridItems[8].value === '0'
      ) {
        return alert('player 2 won')
      } else if (
        this.gridItems[0].value === 'x' &&
        this.gridItems[3].value === 'x' &&
        this.gridItems[6].value === 'x'
      ) {
        return alert('player 1 won')
      } else if (
        this.gridItems[0].value === '0' &&
        this.gridItems[3].value === '0' &&
        this.gridItems[6].value === '0'
      ) {
        return alert('player 2 won')
      } else if (
        this.gridItems[1].value === 'x' &&
        this.gridItems[4].value === 'x' &&
        this.gridItems[7].value === 'x'
      ) {
        return alert('player 1 won')
      } else if (
        this.gridItems[1].value === '0' &&
        this.gridItems[4].value === '0' &&
        this.gridItems[7].value === '0'
      ) {
        return alert('player 2 won')
      } else if (
        this.gridItems[2].value === 'x' &&
        this.gridItems[5].value === 'x' &&
        this.gridItems[8].value === 'x'
      ) {
        return alert('player 1 won')
      } else if (
        this.gridItems[2].value === '0' &&
        this.gridItems[5].value === '0' &&
        this.gridItems[8].value === '0'
      ) {
        return alert('player 2 won')
      } else if (
        this.gridItems[0].value === 'x' &&
        this.gridItems[4].value === 'x' &&
        this.gridItems[8].value === 'x'
      ) {
        return alert('player 1 won')
      } else if (
        this.gridItems[0].value === '0' &&
        this.gridItems[4].value === '0' &&
        this.gridItems[8].value === '0'
      ) {
        return alert('player 2 won')
      } else if (
        this.gridItems[2].value === 'x' &&
        this.gridItems[4].value === 'x' &&
        this.gridItems[6].value === 'x'
      ) {
        return alert('player 1 won')
      } else if (
        this.gridItems[2].value === '0' &&
        this.gridItems[4].value === '0' &&
        this.gridItems[6].value === '0'
      ) {
        return alert('player 2 won')
      }
      if (filteredArr.length === this.gridItems.length) {
        return alert('game over')
      } else {
        return ''
      }
    },
  },
}
</script>

<style lang="scss">
* {
  border-radius: 5px;
  outline: 0px;
}
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  width: 900px;
  height: 900px;
  gap: 20px;
  transition: all 0.4s ease;
}
.grid-item {
  background: #a7eece;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  font-size: 50px;
}

input + div {
  color: white;
  transition: all 0.4s ease;
}
body {
  padding: 0;
  margin: 0;
  min-height: 100vh;
  max-height: fit-content;
}

.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  position: relative;
  align-items: center;
  justify-content: center;
  font-size: 18px;
}
</style>
