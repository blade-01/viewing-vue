<template>
  <form @submit.prevent="submitForm">
    <div class="container">
      <div class="form-content">
        <div class="input-field">
          <label for="name">Name</label>
          <input
            type="text"
            name="name"
            placeholder="Jason Markovich"
            v-model="name"
          />
        </div>
        <div class="input-field">
          <label for="email">Email</label>
          <input
            type="email"
            name="email"
            placeholder="jasonmar@gmail.com"
            required
            v-model="email"
          />
        </div>
        <div class="input-field">
          <label for="password">Password</label>
          <input
            type="password"
            name="password"
            placeholder="xxxxxx"
            v-model="password"
          />
          <div v-if="passwordErr" class="err">{{ passwordErr }}</div>
        </div>
        <div class="input-field">
          <label for="select">Gender:</label>
          <select name="select" id="select" v-model="gender">
            <option value="male">Male</option>
            <option value="female">Female</option>
          </select>
        </div>
        <div class="input-field">
          <label for="skills">Skills</label>
          <input
            type="text"
            name="text"
            placeholder="Skills..."
            v-model="skills"
            @keyup.space="skillType"
            autocomplete="none"
            ref="skill"
          />
          <div
            class="skills"
            v-for="skill in skillArray"
            :key="skill.index"
            @click="delSkill(skill)"
          >
            {{ skill }}
          </div>
        </div>
        <div class="input-field checkboxes">
          <h3>Languages:</h3>
          <div class="checkbox">
            <label for="html">HTML</label>
            <input
              type="checkbox"
              name="html"
              id="html"
              value="html"
              v-model="languages"
            />
          </div>
          <div class="checkbox">
            <label for="css">CSS</label>
            <input
              type="checkbox"
              name="css"
              id="css"
              value="css"
              v-model="languages"
            />
          </div>
          <div class="checkbox">
            <label for="js">JavaScript</label>
            <input
              type="checkbox"
              name="js"
              id="js"
              value="javascript"
              v-model="languages"
            />
          </div>
        </div>
        <div class="checkboxes">
          <label for="terms">Terms and Conditions</label>
          <input
            type="checkbox"
            name="terms"
            id="terms"
            v-model="terms"
            required
          />
        </div>
        <div class="submit-event">
          <input type="submit" value="Creat an Account" />
        </div>
      </div>
    </div>
  </form>

  <div class="output">
    <div class="container">
      <div class="output-content">
        <p>Name: {{ name }}</p>
        <p>Email: {{ email }}</p>
        <p>Password: {{ password }}</p>
        <p>Gender: {{ gender }}</p>
        <p>Languages: {{ languages }}</p>
        <p>Terms: {{ terms }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      password: "",
      gender: "male",
      languages: [],
      terms: "",
      skills: "",
      skillArray: [],
      passwordErr: "",
    };
  },
  methods: {
    skillType() {
      if (this.skills) {
        if (!this.skillArray.includes(this.skills)) {
          this.skillArray.push(this.skills);
        }
        this.skills = "";
      }
    },
    delSkill(skill) {
      this.skillArray = this.skillArray.filter((item) => {
        return skill !== item;
      });
    },
    submitForm() {
      this.passwordErr =
        this.password.length > 5
          ? ""
          : "Password must be at least 6 chars long";
    },
  },
};
</script>

<style scoped>
.form-content {
  background: rgb(230, 255, 248);
  margin: 2rem auto;
  padding: 2rem 1rem;
  border-radius: 10px;
  border: solid 1px black;
}
input {
  display: block;
  width: 100%;
  border-radius: 5px;
  padding: 1rem 0.5rem;
  margin: 0.5rem 0 0;
  outline: none;
  border: solid 1px #888;
}
.input-field {
  margin: 1rem 0;
}
input[type="submit"] {
  width: auto;
  padding: 0.5rem 1rem;
  background: rgb(1, 95, 95);
  color: white;
  font-weight: bolder;
  border-radius: 50px;
  cursor: pointer;
}
.submit-event {
  display: flex;
  justify-content: center;
  margin: 1.5rem 0 0;
}
input[type="checkbox"] {
  display: inline;
  margin: 0 0.5rem;
  width: auto;
  padding: 0;
}
.checkbox,
.checkboxes {
  display: flex;
  align-items: center;
  margin: 0.5rem 0;
}
.output-content {
  background: rgb(230, 255, 248);
  padding: 2rem 1rem;
  border-radius: 10px;
  border: solid 1px black;
}
.output-content p {
  margin: 1rem 0;
}
.skills {
  background: rgb(155, 155, 155);
  color: white;
  border-radius: 20px;
  padding: 0.5rem 1rem;
  display: inline-block;
  margin: 1rem 0.5rem 0 0;
  font-weight: bold;
  cursor: pointer;
}
.err {
  color: red;
  font-size: small;
  margin: 1rem 0 0;
}
</style>
