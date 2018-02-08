<template>
  <div class="admin-post-page">
      <section class="update-form">
          <AdminPostForm :post="loadedPost"/>
      </section>
  </div>
</template>

<script>
import AdminPostForm from '@/components/Admin/AdminPostForm'
export default {
  components: {
      AdminPostForm
  },
  layout: 'admin',
  data() {
      return {
          loadedPost: {
              author: 'Doug',
              title: 'My Awesome Post',
              content: 'Thanks for that',
              thumbnailLink: 'https://articles-images.sftcdn.net/wp-content/uploads/sites/3/2017/05/computerworld_tech_forecast_2017_hottest-tech-skills-for-2017-100692085-large.jpg'
          }
      }
  }
}
</script>

<style scoped>
.update-form {
  width: 90%;
  margin: 20px auto;
}

@media (min-width: 768px) {
  .update-form {
    width: 500px;
  }
}
</style>
