<template>
  <div class="admin-post-page">
      <section class="update-form">
          <AdminPostForm :post="loadedPost" @submit="onSave"/>
      </section>
  </div>
</template>

<script>
import axios from 'axios'
import AdminPostForm from '@/components/Admin/AdminPostForm'
export default {
  components: {
      AdminPostForm
  },
  layout: 'admin',
  asyncData(context) {
    return axios.get('https://nuxt-blog-b05d6.firebaseio.com/posts/' + context.params.postId + '.json')
    .then(res => {
      return {
        loadedPost: res.data,
        postId: context.params.postId
      }
    })
    .catch(e => context.error(e))
  },
  methods: {
    onSave (postData) {
      axios.put('https://nuxt-blog-b05d6.firebaseio.com/posts/' + this.postId + '.json', {
           ...postData, 
           updatedDate: new Date()})
      .then(result => console.log(result))
      .catch(e => console.log(e))
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
