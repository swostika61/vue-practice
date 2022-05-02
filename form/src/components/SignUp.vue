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
    <div className="form-field">
      <label>Skills:(alt+,=>to add the skills)</label>
      <input type="text" v-model="skill" @keyup.alt="addSkills" />
    </div>
    <div className="checkbox-field">
      <input type="checkbox" v-model="term" required />
      <label for="" className="checkbox-label"
        >Accept the terms and condition</label
      >
    </div>
  </form>
  <p>email: {{ email }}</p>
  <p>password: {{ password }}</p>
  <p>role: {{ role }}</p>
  <p>term: {{ term }}</p>
  <p>Skills:
    <ul v-for="s in skills" :key="s">
      <li>{{s}}</li>
    </ul>
  </p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      term: false,
      skill: "",
      skills: [],
    };
  },
  methods: {
    addSkills(e) {
      if (e.key === "," && this.skills) {
        if (!this.skills.includes(this.skill)) {
          this.skills.push(this.skill);
        }
        this.skill=""
      }
    },
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
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.checkbox-field {
  display: flex;
  margin-top: 10px;
}
</style>
