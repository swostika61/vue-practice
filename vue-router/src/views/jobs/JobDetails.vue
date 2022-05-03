<template>
  <div>
    <h1 className="heading">Job Details</h1>
    <p>this is {{id}}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id,
    };
  },
};
</script>

<style></style>
