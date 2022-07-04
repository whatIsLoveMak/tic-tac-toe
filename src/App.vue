<template>
  <div class="app">
    <div class="information">
      <div class="player">
        Сейчас ходит: <span>{{ this.player ? 'Игрок 1' : 'Игрок 2' }}</span>
      </div>
      <div class="score">
        <div class="player">
          <div>Игрок 1 :</div>
          <div class="number">{{ count1 }}</div>
        </div>
        <div class="player">
          <div>Игрок 2 :</div>
          <div class="number">{{ count2 }}</div>
        </div>
      </div>
      <t-button @click.native="surrender" :inner-text="'surrender'" />
    </div>
    <div class="grid">
      <div
        @click="clickPlayer(item)"
        v-for="item in gridItems"
        :key="item.id"
        :class="setImg(item.value)"
      >
        <div>{{ item.value }}</div>
      </div>
    </div>
    <t-modal
      :winner="winner"
      :items="gridItems"
      @close-modal="closeModal"
      v-if="modalView"
    />
  </div>
</template>

<script>
import TModal from '@/components/tModal'
import TButton from '@/UI/tButton'
export default {
  components: { TButton, TModal },
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
      modalView: false,
      count1: 0,
      count2: 0,
    }
  },
  methods: {
    clickPlayer(item) {
      if (item.value === '') {
        this.player ? (item.value = 'x') : (item.value = '0')
        this.player = !this.player
      }
    },
    plusCounter() {
      this.modalView = true
      // this.player ? this.count2++ : this.count1++
    },
    surrender() {
      //this.modalView = true
      //this.player ? this.count2++ : this.count1++
      //this.player = true
    },
    closeModal(value) {
      this.player ? this.count2++ : this.count1++
      this.player = true
      this.modalView = value
      console.log(this.modalView)
    },
    setImg(value) {
      if (value === '0') {
        return 'grid-item circle'
      } else if (value === 'x') {
        return 'grid-item cross'
      } else {
        return 'grid-item'
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
        return true
      } else if (
        this.gridItems[0].value === '0' &&
        this.gridItems[1].value === '0' &&
        this.gridItems[2].value === '0'
      ) {
        return true
      } else if (
        this.gridItems[3].value === 'x' &&
        this.gridItems[4].value === 'x' &&
        this.gridItems[5].value === 'x'
      ) {
        return true
      } else if (
        this.gridItems[3].value === '0' &&
        this.gridItems[4].value === '0' &&
        this.gridItems[5].value === '0'
      ) {
        return true
      } else if (
        this.gridItems[6].value === 'x' &&
        this.gridItems[7].value === 'x' &&
        this.gridItems[8].value === 'x'
      ) {
        return true
      } else if (
        this.gridItems[6].value === '0' &&
        this.gridItems[7].value === '0' &&
        this.gridItems[8].value === '0'
      ) {
        return true
      } else if (
        this.gridItems[0].value === 'x' &&
        this.gridItems[3].value === 'x' &&
        this.gridItems[6].value === 'x'
      ) {
        return true
      } else if (
        this.gridItems[0].value === '0' &&
        this.gridItems[3].value === '0' &&
        this.gridItems[6].value === '0'
      ) {
        return true
      } else if (
        this.gridItems[1].value === 'x' &&
        this.gridItems[4].value === 'x' &&
        this.gridItems[7].value === 'x'
      ) {
        return true
      } else if (
        this.gridItems[1].value === '0' &&
        this.gridItems[4].value === '0' &&
        this.gridItems[7].value === '0'
      ) {
        return true
      } else if (
        this.gridItems[2].value === 'x' &&
        this.gridItems[5].value === 'x' &&
        this.gridItems[8].value === 'x'
      ) {
        return true
      } else if (
        this.gridItems[2].value === '0' &&
        this.gridItems[5].value === '0' &&
        this.gridItems[8].value === '0'
      ) {
        return true
      } else if (
        this.gridItems[0].value === 'x' &&
        this.gridItems[4].value === 'x' &&
        this.gridItems[8].value === 'x'
      ) {
        return true
      } else if (
        this.gridItems[0].value === '0' &&
        this.gridItems[4].value === '0' &&
        this.gridItems[8].value === '0'
      ) {
        return true
      } else if (
        this.gridItems[2].value === 'x' &&
        this.gridItems[4].value === 'x' &&
        this.gridItems[6].value === 'x'
      ) {
        return true
      } else if (
        this.gridItems[2].value === '0' &&
        this.gridItems[4].value === '0' &&
        this.gridItems[6].value === '0'
      ) {
        return true
      }
      if (filteredArr.length === this.gridItems.length) {
        return alert('game over')
      } else {
        return ''
      }
    },
    winner() {
      if (this.player == true) {
        return 'Игрок 2'
      } else {
        return 'Игрок 1'
      }
    },
  },
  watch: {
    endGame() {
      this.plusCounter()
    },
  },
}
</script>

<style lang="scss">
* {
  border-radius: 5px;
  outline: 0px;
}
.player {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  & span {
    color: red;
    font-size: 25px;
  }
}
.number {
  font-size: 30px;
  font-weight: 600;
  color: red;
}
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  width: 800px;
  height: 800px;
  gap: 20px;
  transition: all 0.4s ease;
}
.score {
  display: flex;
  flex-direction: row;
  gap: 30px;
}
.button {
  padding: 10px 20px;
  margin-bottom: 30px;
  cursor: pointer;
  background: #a7eece;
  box-shadow: 5px 5px 10px #2a4b41;
  transition: all 0.4s ease;
  color: white;
  font-size: 20px;
  font-weight: 600;
  border: none;
  &:hover {
    box-shadow: 0px 0px 0px #2a4b41;
  }
}
.grid-item {
  background: #a7eece;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  font-size: 0px;
  box-shadow: 5px 5px 10px #2a4b41;
  transition: all 0.4s ease;
  cursor: pointer;
  &:hover {
    box-shadow: 0px 0px 0px #2a4b41;
  }
}
.circle {
  background-image: url('./img/circle.png');
  background-position: center;
  background-repeat: no-repeat;
  background-color: #a7eece;
}
.cross {
  background-image: url('./img/cross.png');
  background-position: center;
  background-repeat: no-repeat;
  background-color: #a7eece;
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
  flex-direction: row-reverse;
  position: relative;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  gap: 30px;
}
</style>
