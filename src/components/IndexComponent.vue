<template>
  <div>
    <h1>Community Posts</h1>
    <div class="post-container">
      <div v-for="post in posts" :key="post._id" class="post-card">
        <h2>{{ post.title }}</h2>
        <p>{{ post.body }}</p>
        <div class="actions">
          <router-link :to="{name: 'edit', params: { id: post._id }}" class="btn btn-edit">Edit</router-link>
          <button @click.prevent="deletePost(post._id)" class="btn btn-delete">Delete</button>
        </div>
      </div>
    </div>
    <router-link :to="{ name: 'create' }" class="btn btn-create">Create New Post</router-link>
  </div>
</template>

<script>
  export default {
      data() {
        return {
          posts: []
        }
      },
      created() {
      let uri = 'http://localhost:4000/posts';
      this.axios.get(uri).then(response => {
        this.posts = response.data;
      });
    },
    methods: {
      deletePost(id)
      {
        let uri = `http://localhost:4000/posts/delete/${id}`;
        this.axios.delete(uri).then(() => {
            this.posts.splice(this.posts.indexOf(id), 1);
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
.post-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.post-card {
  background: #fff;
  border: 1px solid #dedede;
  padding: 1rem;
  border-radius: 0.5rem;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

.actions {
  display: flex;
  justify-content: space-between;
  margin-top: 1rem;
}

.btn {
  border: none;
  padding: 0.5rem 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn-edit {
  background-color: #ffc107;
}

.btn-delete {
  background-color: #dc3545;
}

.btn-create {
  background-color: #28a745;
  color: white;
  display: block;
  width: max-content;
  margin-top: 1rem;
}

.btn:hover {
  opacity: 0.9;
}
</style>