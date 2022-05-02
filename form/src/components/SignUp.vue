<template>
  <form action="">
    <div className="form-field">
      <label>Email:</label>
      <input type="text" required v-model="email" />
    </div>
    <div className="form-field">
      <label>Password:</label>
      <input type="password" required v-model="password" />
    </div>
    <div className="form-field">
      <label for=""> Role:</label>
      <select v-model="role">
        <option value="developer">Web developer</option>
        <option value="designer">Web designer</option>
      </select>
    </div>
  </form>
  <p>email: {{ email }}</p>
  <p>password: {{ password }}</p>
  <p>role:  {{role}}</p>
</template>

<script>
export default {
  data() {
    return { email: "", password: "",role:"" };
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
.form-field {
  margin-bottom: 10px;
}
label {
  display: flex;
  margin-bottom: 5px;
  color: rgb(130, 125, 125);
}
input,
select {
  width: 80%;
  display: block;
  padding: 10px 6px;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
</style>
