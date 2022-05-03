<template>
  <div>
    <h1 className="heading">Job Details</h1>
    <h2>{{ job.title }}</h2>
    <p>
      {{ job.details }}
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id,
      job: [],
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
