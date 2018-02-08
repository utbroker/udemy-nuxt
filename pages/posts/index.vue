<template>
  <div class="posts-page">
    <PostList :posts="loadedPosts"/>
  </div>
</template>

<script>
import PostList from '@/components/Posts/PostList'

export default {
  components: {
    PostList
  },
  asyncData(context, callback) {
    setTimeout(() => {
      callback(null, {
      loadedPosts: [
        {
          id: '1',
          title: "First Post",
          previewText: "This is our first post!",
          thumbnail: "https://articles-images.sftcdn.net/wp-content/uploads/sites/3/2017/05/computerworld_tech_forecast_2017_hottest-tech-skills-for-2017-100692085-large.jpg"
        },
        {
          id: '2',
          title: "Second Post",
          previewText: "This is our second post!",
          thumbnail: "https://articles-images.sftcdn.net/wp-content/uploads/sites/3/2017/05/computerworld_tech_forecast_2017_hottest-tech-skills-for-2017-100692085-large.jpg"
        }
      ]
    })
    }, 1500)
  }
}
</script>

<style scoped>
.posts-page {
    display: flex;
    justify-content: center;
    align-items: center;
}

</style>

