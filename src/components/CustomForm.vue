<template>
  <form @submit.prevent="submitData" class="form-content">
    <label id="lblEmail" for="email">EMAIL:</label>
    <input name="email" id="email" type="email" v-model="email" required />

    <label id="lblPassword" for="password">PASSWORD:</label>
    <input
      name="password"
      id="password"
      type="password"
      v-model="password"
      required
    />
    <div class="error" v-if="passwordError">{{ passwordError }}</div>

    <label id="lblRole" for="role">ROLE:</label>
    <select class="role-class" name="role" id="role" v-model="role" required>
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label id="lblSkills" for="skills">SKILLS:</label>
    <input
      name="skills"
      id="skills"
      type="text"
      v-model="tempSkill"
      @keyup="addSkill"
    />
    <div class="crumbs-container">
      <div v-for="skill in skills" :key="skill" class="crumbs">
        <p class="crumbs-skill">{{ skill }}</p>
        <span
          class="material-symbols-outlined"
          @click="removeSkill($event, skill)"
        >
          close
        </span>
      </div>
    </div>

    <div class="terms-conditions-container">
      <input
        name="terms"
        id="terms"
        class="terms-conditions"
        v-model="terms"
        type="checkbox"
      />
      <label id="lblTerms" for="terms">ACCEPT TERMS AND CONDITIONS</label>
    </div>

    <button>Create Account</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "designer",
      terms: false,
      tempSkill: "",
      skills: [],
      passwordError: "",
      formData: {
        dataEmail: "",
        dataPassword: "",
        dataRole: "",
        dataSkills: "",
        dataTerms: false,
      },
    };
  },
  methods: {
    submitData(e) {
      this.passwordError =
        this.password.length > 5
          ? ""
          : "Password must be more than 5 characters";
      if (!this.passwordError) {
        this.formData.dataEmail = this.email;
        this.formData.dataPassword = this.password;
        this.formData.dataRole = this.role;
        this.formData.dataSkills = this.skills;
        this.formData.dataTerms = this.terms;
        console.log(this.formData);
      }
    },
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        const tempSkill = this.tempSkill.split(",")[0];
        if (!this.skills.includes(tempSkill)) {
          this.skills.push(tempSkill);
        }
        this.tempSkill = "";
      }
    },
    removeSkill(e, skill) {
      const result = this.skills.filter((item) => {
        return item !== skill;
      });
      this.skills = result;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500;700&display=swap");

.material-symbols-outlined {
  font-variation-settings: "FILL" 0, "wght" 500, "GRAD" 0, "opsz" 48;
  font-size: 15px;
  cursor: pointer;
  margin-left: 10px;
}

.form-content {
  display: flex;
  flex-direction: column;
  align-items: start;
  font-family: "Rubik", Helvetica, Arial, sans-serif;
  padding: 20px;
  color: #575757bf;
  font-size: 14px;
}
*:focus {
  outline: none;
  box-shadow: 0 0 0 0.4rem hsla(200, 3%, 19%, 0.229);
}
label {
  margin-top: 15px;
  margin-bottom: 10px;
}
input,
.role-class {
  width: 100%;
  height: 40px;
  margin-bottom: 10px;
  text-indent: 10px;
  border: none;
  font-family: "Rubik", Helvetica, Arial, sans-serif;
  background: #eeeeee9d;
}
button {
  height: 40px;
  background: #000;
  width: 100%;
  border: none;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #eee;
  cursor: pointer;
  margin-top: 30px;
  font-size: 14px;
}
.terms-conditions {
  width: 15px;
  height: 15px;
  margin-bottom: -3.5px;
}

.terms-conditions-container {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 20px;
}
.crumbs {
  background-color: rgba(212, 212, 202, 0.526);
  background-color: #fff;
  border-style: solid;
  border-width: 1px;
  border-color: rgba(0, 0, 0, 0.384);
  display: flex;
  align-items: center;
  padding: 5px 10px 5px 20px;
  border-radius: 20px;
  margin-bottom: 2px;
  font-weight: bold;
  width: fit-content;
}
.crumbs-skill {
  font-size: 12px;
  color: #717171;
}
.crumbs-container {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  column-gap: 5px;
}
.error {
  color: crimson;
}
</style>
