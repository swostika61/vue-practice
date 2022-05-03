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
      jobs: [
        {
          title: "Web designer",
          id: 1,
          details:
            "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quo, earum!",
        },
        {
          title: "Web Developer",
          id: 2,
          details:
            "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quo, earum!",
        },
        {
          title: "DevOps",
          id: 3,
          details:
            "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Quo, earum!",
        },
      ],
    };
  },
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
 a{
  text-decoration: none;
}
.job-title:hover {
  background: #b7b6b6;
}
.heading {
  color: #70844d;
}
</style>
