<template>
  <div>
    <h1 className="heading">Jobs</h1>
    <div v-for="job in jobs" :key="job.id">
      <router-link :to="{ name: 'jobDetails', params: { id: job.id } }">
        <h4 class="job-title">{{ job.title }}</h4>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      jobs: [],
    };
  },
  mounted(){
    fetch('http://localhost:3000/jobs')
  .then(response => response.json())
  .then(data => this.jobs=data);

  }
};
</script>

<style>
.job-title {
  color: #653e71;
  cursor: pointer;
  background: #c1c1c1;
  padding: 10px;
  width: 200px;
  margin: 20px auto;
  text-align: center;
  border-radius: 8px;
}
a {
  text-decoration: none;
}
.job-title:hover {
  background: #b7b6b6;
}
.heading {
  color: #70844d;
}
</style>
