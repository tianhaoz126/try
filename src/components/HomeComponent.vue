<template>
  <div class="container">
    <div class="hero">
      <h1>Welcome to the Data Science Community</h1>
      <p>Explore, Share, and Grow with Data.</p>
    </div>
     
     <div class="video-container">
      <iframe
        width="560"
        height="315"
        src="https://www.youtube.com/embed/N6BghzuFLIg?si=OpbNR3yuIIeWdEkX"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        allowfullscreen>
      </iframe>
    </div>

    <section class="features">
      <div class="feature">
        <i class="fas fa-chart-line"></i>
        <h2>Insightful Analytics</h2>
        <p>Delve into datasets with our powerful analytical tools.</p>
      </div>
      <div class="feature">
        <i class="fas fa-project-diagram"></i>
        <h2>Collaborative Projects</h2>
        <p>Collaborate on projects with peers from around the globe.</p>
      </div>
      <div class="feature">
        <i class="fas fa-brain"></i>
        <h2>Machine Learning</h2>
        <p>Engage with machine learning models and learn from shared knowledge.</p>
      </div>
    </section>

    <section class="latest-discussions">
      <h2>Latest Discussions</h2>
      <div class="discussion">
        <div class="discussion-content">
          <h3>Discussion Title</h3>
          <p>Description of the discussion topic...</p>
          <button>Join Discussion</button>
        </div>
        <div class="discussion-stats">
          <span><i class="fas fa-users"></i> 24 Participants</span>
          <span><i class="fas fa-comments"></i> 76 Comments</span>
        </div>
      </div>
      <!-- Repeat for other discussions -->
    </section>
  </div>
</template>

<script>
export default {
  name: 'HomeComponent'
}
</script>

<style scoped>
.container {
  max-width: 1200px;
  margin: auto;
}

.hero {
  text-align: center;
  padding: 50px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
}

.features {
  display: flex;
  justify-content: space-around;
  text-align: center;
  padding: 20px;
}

.feature i {
  font-size: 48px;
  margin-bottom: 10px;
}

.latest-discussions h2 {
  padding: 20px;
  background-color: #f7f7f7;
}

.discussion {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
  padding: 20px;
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.discussion-content {
  flex: 3;
}

.discussion-stats {
  flex: 1;
  text-align: right;
}

button {
  background-color: #667eea;
  color: white;
  border: none;
  padding: 10px 20px;
  margin-top: 10px;
  cursor: pointer;
}

button:hover {
  background-color: #5a67d8;
}
/* Styles for the video container to make it responsive */
.video-container {
  position: relative;
  overflow: hidden;
  padding-top: 56.25%; /* 16:9 Aspect Ratio */
}

.video-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

</style>
