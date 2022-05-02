<template>
  <form action="">
    <label>Email:</label>
    <input type="text" required v-model="email" />
  </form>
  <p>{{ email }}</p>
</template>

<script>
export default {
  data() {
    return { email: "" };
  },
};
</script>

<style>
form {
  width: 450px;
  background: #fff;
  margin: auto;
  padding: 30px 20px;
  display: flex;
  border-radius: 10px;
  flex-direction: column;
}
label {
  display: flex;
  margin-bottom: 5px;
  color: rgb(130, 125, 125);
}
input {
  width: 80%;
  padding: 6px 10px;
  margin-bottom: 10px;
}
</style>
