<template>
  <form @submit.prevent="handleSubmit" class="form-control">
    <h1>Create an Acount</h1>
    <label>
      Email:
    </label>
    <input type="email" required v-model="email" />

    <label>
      Password:
    </label>
    <input type="password" required v-model="password" />
    <div v-if="passwordError" class="error">{{ passwordError }}</div>

    <label>Role:</label>
    <select v-model="role" placeholder="Select your role">
      <option value="FrontendDeveloper">Frontend Developer</option>
      <option value="BackendDeveloper">Backend Developer</option>
      <option value="FullstackDeveloper">Fullstack Developer</option>
      <option value="Designer">Web Designer</option>
      <option value="Tester">Web Tester</option>
    </select>

    <label>Skills:</label>
    <input
      type="text"
      placeholder="Write and press Alt"
      v-model="tempSkill"
      @keyup="addSkill"
      class="skills"
    />
    <div
      v-for="skill in skills"
      :key="skill"
      class="pill"
      @click="removeSkill(skill)"
    >
      {{ skill }}
    </div>

    <div class="terms">
      <input type="checkbox" required v-model="terms" />
      <label class="accept">Accept terms and conditions</label>
      <br />
      <input type="checkbox" v-model="allow" />
      <label>Allow sending advertising emails</label>
    </div>

    <!-- <div>
      <input type="checkbox" value="shaun" v-model="names" />
      <label>Shaun</label>
    </div>
    <div>
      <input type="checkbox" value="hawk" v-model="names" />
      <label>Hawk</label>
    </div>
    <div>
      <input type="checkbox" value="jack" v-model="names" />
      <label>Jack</label>
    </div> -->

    <div class="submit">
      <button class="ripple">
        Sign Up
      </button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "@gmail.com",
      password: "",
      role: "developer",
      terms: false,
      //   names: [],
      tempSkill: "",
      skills: [],
      passwordError: "",
      allow: false,
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "Alt" && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
          this.tempSkill = "";
        }
      }
    },
    removeSkill(skill) {
      this.skills = this.skills.filter(function(item) {
        return skill !== item;
      });
    },
    handleSubmit() {
      this.passwordError =
        this.password.length > 5
          ? ""
          : "Your password must be at least 6 chars long";

      if (!this.passwordError) {
        console.log(" email: ", this.email);
        console.log(" password: ", this.password);
        console.log(" role: ", this.role);
        console.log(" skills: ", this.skills);
        console.log(" terms accepted: ", this.terms);
        console.log(" advertising emails: ", this.allow);
      }
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  background-color: #fff;
  text-align: left;
  padding: 10px 70px;
  border-radius: 5px;
  position: relative;
  z-index: 5;
  box-shadow: rgba(255, 255, 255, 0.1) 0px 1px 1px 0px inset,
    rgba(50, 50, 93, 0.25) 0px 50px 100px -20px,
    rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
}
.error {
  color: fuchsia;
  margin-top: 10px;
  font-weight: bold;
}
h1 {
  font-family: Arial Black;
}
label {
  color: #000;
  display: inline-block;
  margin: 25px 5px 10px;
  font-size: 0.8em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}

form :is(label:last-of-type, label.accept) {
  text-transform: inherit;
}

input,
select {
  display: block;
  padding: 5px 6px;
  width: 100%;
  border: none;
  outline: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
input[type="checkbox"] {
  display: inline-block;
  width: 15px;
  position: relative;
  margin: 0 10px 0 0;
  top: 3px;
}
.pill {
  background-color: #60bfff;
  border-radius: 10px;
  color: #000;
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  font-size: 12px;
  cursor: pointer;
  text-transform: uppercase;
}

/* button {
  background-color: #0000ff;
  border: 0;
  padding: 10px 20px;
  color: white;
  border-radius: 5px;
  margin-top: 35px;
  cursor: pointer;
  font-weight: bold;
  letter-spacing: 1px;
} */
.submit {
  text-align: center;
}
button.ripple {
  background-color: #0000ff;
  color: #fff;
  border: none;
  font-size: 16px;
  text-transform: uppercase;
  letter-spacing: 2px;
  padding: 20px 30px;
  overflow: hidden;
  margin: 0px auto;
  margin-top: 50px;
  margin-bottom: 20px;
  display: block;
  position: relative;
  cursor: pointer;
  border-radius: 5px;
}

button:focus {
  outline: none;
  border: none;
}

button .circle {
  position: absolute;
  background-color: #fff;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  transform: translate(-50%, -50%) scale(0);
  animation: scale 0.5s ease-out;
}

@keyframes scale {
  to {
    transform: translate(-50%, -50%) scale(3);
    opacity: 0;
  }
}
</style>
