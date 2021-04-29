<template>
  <form @submit.prevent="handleSubmit">
    <label for="email">Email:</label>
    <input type="email" required v-model="email" />
    <label for="password">Password:</label>
    <input type="password" required v-model="password" />
    <div class="error">
      {{ passwordError }}
    </div>
    <label for="skils">Skils:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>
    <div class="">
      <label>Name1</label>
      <input type="checkbox" value="name1" v-model="names" />
    </div>
    <div class="">
      <label>Name2</label>
      <input type="checkbox" value="name2" v-model="names" />
    </div>
    <div class="">
      <label>Name3</label>
      <input type="checkbox" value="name3" v-model="names" />
    </div>

    <div class="submit">
      <button>Create an Account</button>
    </div>
  </form>
  <p class="">Email: {{ email }}</p>
  <p class="">Password: {{ password }}</p>
  <p class="">Names: {{ names }}</p>
</template>

<script>
export default {
  name: "SignupForm",
  props: [],
  data() {
    return {
      email: "default.value@gmail.com",
      password: "",
      names: [],
      tempSkill: "",
      skills: [],
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }

        this.tempSkill = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => item !== skill);
    },
    handleSubmit() {
      console.log("form submitted");
      //validate password
      this.passwordError = this.password.length > 5 ? "" : "Password too short";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: white;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}
.submit {
  text-align: center;
}
button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}
.error {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>
