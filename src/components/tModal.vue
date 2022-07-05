<template>
  <div class="modal-body">
    <div class="modal-content">
      <div class="title" v-if="winner !== 'Ничья'">Победил {{ winner }}</div>
      <div class="title" v-else>{{ winner }}</div>
      <t-button @click.native="newGame" :inner-text="'new game'" />
    </div>
  </div>
</template>

<script>
import TButton from '@/UI/tButton'
export default {
  name: 'tModal',
  components: { TButton },
  data() {
    return {
      elem: false,
    }
  },
  props: {
    winner: {
      type: String,
      default: '',
    },
    items: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    newGame() {
      this.items.forEach((item) => (item.value = ''))
      this.$emit('close-modal', false)
    },
  },
}
</script>

<style scoped>
.modal-body {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  background: rgba(0, 0, 0, 0.5);
}
.modal-content {
  width: 400px;
  height: 400px;
  background: white;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.title {
  font-size: 25px;
  font-weight: 600;
  margin-bottom: 30px;
}
</style>
