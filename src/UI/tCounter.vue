<template>
  <div class="number">{{ count }}</div>
</template>

<script>
export default {
  name: 'tCounter',
  data() {
    return {
      count: 0,
    }
  },
}
</script>

<style scoped>
.number {
  font-size: 30px;
  font-weight: 600;
  color: red;
}
</style>
