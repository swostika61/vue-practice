<template>
  <div>
    <div v-if="job">
      <h1 className="heading">Job Details</h1>
      <h2>{{ job.title }}</h2>
      <p>
        {{ job.details }}
      </p>
    </div>
    <div v-else>
      <p>no jobs available</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id,
      job: null,
    };
  },
  mounted() {
    fetch(`http://localhost:3000/jobs/${this.id}`)
      .then((response) => response.json())
      .then((data) => (this.job = data));
  },
};
</script>

<style></style>
