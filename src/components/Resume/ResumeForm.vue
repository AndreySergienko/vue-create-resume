<template>
  <form class="card card-w30" @submit.prevent="createBlockResume">
    <AppSelect
      :options="optionsSelect"
      :selected="typeBlock"
      @change="setTypeBlock"
    />

    <AppTextArea
      :textAreaField="textBlock"
      @input="setTextBlock"
    />

    <button class="btn primary" :disabled="isValid">Добавить</button>
  </form>
</template>

<script>
import AppSelect from "../AppSelect"
import AppTextArea from "../AppTextArea"
export default {
  emits: ['submit'],
  data() {
    return {
      optionsSelect: [
        {
          value: 'Title',
          text: 'Заголовок'
        },
        {
          value: 'Subtitle',
          text: 'Подзаголовок'
        },
        {
          value: 'Avatar',
          text: 'Аватар'
        },
        {
          value: 'Text',
          text: 'Текст'
        }
      ],
      typeBlock: 'title',
      textBlock: '',
    }
  },
  methods: {
    createBlockResume() {
      const data = {
        type: this.typeBlock,
        text: this.textBlock
      }
      this.$emit('submit', data)

      // clear field
      this.typeBlock = 'title'
      this.textBlock = ''
    },
    setTypeBlock(value) {
      return this.typeBlock = value
    },
    setTextBlock(value) {
      return this.textBlock = value
    },
  },
  computed: {
    isValid() {
      if (this.typeBlock && this.textBlock.length < 3) {
        return true
      } else {
        return false
      }
    }
  },
  components: {
    AppSelect,
    AppTextArea
  }
}
</script>
