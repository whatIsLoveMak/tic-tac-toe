<template>
  <button class="button">{{ innerText }}</button>
</template>

<script>
export default {
  name: 'tButton',
  props: {
    innerText: {
      type: String,
      default: '',
    },
  },
}
</script>

<style scoped></style>
