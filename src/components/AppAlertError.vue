<template>
  <div class="alert danger" @click="closeAlert">
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  emits: ['close'],
  props: {
    message: {
      type: String,
      required: true
    }
  },
  computed: {
    closeAlert() {
     return this.$emit('close')
    }
  }
}
</script>

<style scoped>
</style>
