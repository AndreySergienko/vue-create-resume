<template>
  <div class="container column">

    <ResumeForm
      @submit="setResumeList"
    />

    <ResumeCard
      :resumeList="resumeList"
    />
  </div>

  <div class="container">
    <p>
      <button class="btn primary" @click="loadingComments" :disabled="isValid">Загрузить комментарии</button>
    </p>

    <AppAlertError
      v-show="errorMessage"
      :message="errorMessage"
      @close="closeAlert"
    />

    <AppLoader v-if="isLoading"/>
    <ResumeComments
      v-if="commentsList.length"
      :comments="commentsList"
    />

    <h3 class="white-color" v-if="noComments">Комментариев пока нет</h3>
  </div>
</template>

<script>
import ResumeCard from "./components/Resume/ResumeCard"
import ResumeForm from "./components/Resume/ResumeForm"
import ResumeComments from "./components/Resume/ResumeComments"
import AppLoader from "./components/AppLoader"
import AppAlertError from "./components/AppAlertError"

export default {
  data() {
    return {
      isLoading: false,
      commentsList: [],
      resumeList: [],
      errorMessage: '',
    }
  },
  methods: {
    setResumeList(value) {
      this.resumeList.push(value)
    },

    async loadingComments() {
      this.isLoading = true
      try {
        const response = await fetch(process.env.VUE_APP_COMMENTS_URL)
        const data = await response.json()
        this.commentsList = Object.keys(data).map(key => {
          return {
            id: key,
            ...data[key]
          }
        })
      } catch (e) {
        this.errorMessage = e.message
      } finally {
        this.isLoading = false
      }
    },
    closeAlert() {
      return this.errorMessage = ''
    }
  },
  computed: {
    noComments() {
      return !this.isLoading && !this.commentsList.length
    },
    isValid() {
      return !!this.commentsList.length
    }
  },
  components: {
    ResumeForm,
    AppAlertError,
    AppLoader,
    ResumeComments,
    ResumeCard,
  }
}
</script>

<style scoped>
.white-color {
  color: #fff;
  text-align: center;
}
</style>
