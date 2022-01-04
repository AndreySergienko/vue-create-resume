<template>
  <div class="form-control">
    <label for="type">{{ label }}</label>
    <select id="type" @input="changeSelected">
      <option v-for="option in options"  :value="option.value" :selected="selected === option.value">{{ option.text }}</option>
    </select>
  </div>
</template>

<script>
  export default {
    emits: ['change'],
    props: {
      options: {
        type: Array,
        required: true
      },
      selected: {
        type: String,
        requireD: true
      },
      label: {
        type: String,
        required: false,
        default: 'Тип блока'
      }
    },
    methods: {
      changeSelected(e) {
        return this.$emit('change', e.target.value)
      }
    }
  }
</script>

<style>

</style>
