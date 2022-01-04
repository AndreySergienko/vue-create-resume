<template>
  <div class="card card-w70">

    <h3 v-if="!resumeList.length">Добавьте первый блок, чтобы увидеть результат</h3>
    <component
      v-else
      v-for="resume in resumeList"
      :is="'resume-' + resume.type"
      :key="resume.type"
      v-bind="{text: resume.text}"
    ></component>
  </div>
</template>

<script>
import ResumeAvatar from "../ResumePart/ResumeAvatar"
import ResumeTitle from "../ResumePart/ResumeTitle"
import ResumeSubtitle from "../ResumePart/ResumeSubtitle"
import ResumeText from "../ResumePart/ResumeText"

export default {
  props: {
    resumeList: {
      type: Array,
      required: true
    }
  },
  components: {
    ResumeAvatar,
    ResumeSubtitle,
    ResumeTitle,
    ResumeText
  }
}
</script>
