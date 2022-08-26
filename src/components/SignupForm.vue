<template>
  <!-- The net ninja github branch: lessson44 -->
  <!-- (https://github.com/iamshaunjp/Vue-3-Firebase/blob/lesson-44/web-forms/src/App.vue) -->

  <div>
    <!-- PROBLEM: add an text input field where the user can add
    several skills -->
    <form>
      <label>Email:</label>
      <input type="email" v-model="email" required />
      <label>Password:</label>
      <input type="password" v-model="password" required />
      <label>Role:</label>
      <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer">Web Designer</option>
      </select>
      <!-- 1) Create input field. Add v-model to input
      and set it to "tempSkill". This will contain the
      value the user types in and I´m going to add it
      to an array with all the values the user typed. -->
      <label>Skills (press alt + comma to add):</label>
      <!-- 4) Add keyup event and set it to the funcion addSkill -->
      <!-- 10) Add event modifier alt to the keyup event so that
      the comma the user types does not appear in the screen
      and does not go to our array. IMPORTANT: the alt modifier
      is not working. I don´t know if it´s because mac keyboard
      or due to event modifiers with keyup in vue -->
      <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
      <!-- 9) Output all the skills the user entered. Use the skill
      itself as a key for the list.  -->
      <div v-for="skill in skills" :key="skill" class="pill">
        <span>{{ skill }}</span>
      </div>
      <div class="terms">
        <input type="checkbox" v-model="terms" required />
        <label>Accept terms and conditions</label>
      </div>
    </form>
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "designer",
      terms: false,
      // 2) Add the variable to data
      tempSkill: "",
      // 3) Store all the skillls the user enters inside array
      skills: [],
    };
  },
  methods: {
    /* 5)Create addSkill function and take in the event
object into the funcion. This event we get automatically
when an even fires  */
    addSkill($event) {
      /* 6)Listen to that event on if user types comma
      and if tempSkill has a value */
      if ($event.key === "," && this.tempSkill) {
        /* 7) Take the value in tempSkill and add it
        to the skills array only if it´s not already
        in the array. This prevents the user entering
        the same data twice*/
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        /* 8) Clear thetempSkill variable */
        this.tempSkill = "";
      }
    },
  },
};
</script>

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
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
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
</style>
