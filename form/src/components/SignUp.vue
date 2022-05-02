<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <div className="form-field">
        <label>Email:</label>
        <input type="text" required v-model="email" />
      </div>
      <div className="form-field">
        <label>Password:</label>
        <input type="password" required v-model="password" />
        <p v-if="passwordError" className="error">{{ passwordError }}</p>
      </div>
      <div className="form-field">
        <label for=""> Role:</label>
        <select v-model="role" required>
          <option value="developer">Web developer</option>
          <option value="designer">Web designer</option>
        </select>
      </div>
      <div className="form-field">
        <label>Skills:(alt+,=>to add the skills)</label>
        <input type="text" v-model="skill" @keyup.alt="addSkills" />
        <div v-for="s in skills" :key="s" className="skill">
          <span @click="deleteSkill(s)">{{ s }}</span>
        </div>
      </div>
      <div className="checkbox-field">
        <input type="checkbox" v-model="term" required />
        <label for="" className="checkbox-label"
          >Accept the terms and condition</label
        >
      </div>
      <div className="submit">
        <button className="btn">create account</button>
      </div>
    </form>
    <p>email: {{ email }}</p>
    <p>password: {{ password }}</p>
    <p>role: {{ role }}</p>
    <p>term: {{ term }}</p>
  </div>
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
      passwordError: "",
    };
  },
  methods: {
    addSkills(e) {
      if (e.key === "," && this.skills) {
        if (!this.skills.includes(this.skill)) {
          this.skills.push(this.skill);
        }
        this.skill = "";
      }
    },
    deleteSkill(s) {
      this.skills = this.skills.filter((skill) => skill !== s);
    },
    handleSubmit() {
      console.log("handling submit");
      console.log("email: ", this.email);
      console.log("password: ", this.password);
      console.log("role: ", this.role);
      console.log("skills: ", this.skills);
      console.log("terms accepted: ", this.term);
      this.passwordError =
        this.password.length > 5
          ? ""
          : "Password must be at least 6 characters long";
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
  text-align: left;
  border-radius: 10px;
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
.skill {
  display: inline-block;
  background: beige;
  color: #737678;
  padding: 5px;
  margin-right: 8px;
  margin-top: 10px;
  border-radius: 10px;
  justify-content: flex-start;
  cursor: pointer;
}
.submit {
  text-align: center;
  margin-top: 5px;
}
.btn {
  border-radius: 20px;
  border: none;
  background: #483d8b;
  color: #fff;
  font-size: 15px;
  text-transform: capitalize;
  padding: 8px 20px;
}
.error {
  color: rgb(240, 44, 44);
  font-size: 15px;
  text-transform: capitalize;
}
</style>
