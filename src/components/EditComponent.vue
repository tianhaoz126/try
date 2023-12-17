<template>
  <div class="edit-post-container">
    <h1>Edit Post</h1>
    <form @submit.prevent="updatePost" class="edit-post-form">
      <div class="form-group">
        <label for="postTitle">Post Title</label>
        <input id="postTitle" type="text" class="form-control" v-model="post.title">
      </div>
      <div class="form-group">
        <label for="postBody">Post Body</label>
        <textarea id="postBody" class="form-control" v-model="post.body" rows="5"></textarea>
      </div>
      <button type="submit" class="btn-update">Update</button>
    </form>
  </div>
</template>

<script>
    export default {

      data() {
        return {
          post: {}
        }
      },
      created() {
        let uri = `http://localhost:4000/posts/edit/${this.$route.params.id}`;
        this.axios.get(uri).then((response) => {
            this.post = response.data;
        });
      },
      methods: {
        updatePost() {
          let uri = `http://localhost:4000/posts/update/${this.$route.params.id}`;
          this.axios.post(uri, this.post).then(() => {
            this.$router.push({name: 'posts'});
          });
        }
      }
    }
</script>

<style scoped>
.edit-post-container {
  max-width: 700px;
  margin: 2rem auto;
  background: #fff;
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
h1 {
  color: #333;
  text-align: center;
  margin-bottom: 1.5rem;
}
.form-group {
  margin-bottom: 1rem;
}
label {
  display: block;
  margin-bottom: .5rem;
  color: #666;
}
input, textarea {
  width: 100%;
  padding: 0.5rem;
  border-radius: 4px;
  border: 1px solid #ddd;
  margin-bottom: 1rem;
}
.btn-update {
  background-color: #5cb85c;
  color: white;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.btn-update:hover {
  background-color: #4cae4c;
}
</style>