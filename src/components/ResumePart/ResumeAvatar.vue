<template>
  <div class="avatar">
<!--    https://cdn.dribbble.com/users/5592443/screenshots/14279501/drbl_pop_r_m_rick_4x.png -->
    <img :src="$attrs.text">
  </div>
</template>
<script>
export default {}
</script>
<style scoped>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
