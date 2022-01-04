<template>
  <div class="form-control">
    <label for="value">{{ label }}</label>
    <textarea id="value" :rows="rows" :value="textAreaField" @input="inputText"></textarea>
  </div>
</template>

<script>
export default {
  emits: ['input'],
  props: {
    textAreaField:{
      type: String,
      required: true
    },
    rows: {
      type: Number,
      required: false,
      default: 5
    },
    label: {
      type: String,
      required: false,
      default: 'Значение'
    }
  },
  methods: {
    inputText(e) {
      this.$emit('input', e.target.value)
    }
  }
}
</script>

<style></style>
