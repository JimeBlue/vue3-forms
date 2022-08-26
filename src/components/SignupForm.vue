<template>
  <!-- The net ninja github branch: lessson44 -->
  <!-- (https://github.com/iamshaunjp/Vue-3-Firebase/blob/lesson-44/web-forms/src/App.vue) -->

  <div>
    <form>
      <!-- EXPLANATION: when the user clicks on an skill, it should be
      deleted -->
      <label>Email:</label>
      <input type="email" v-model="email" required />
      <label>Password:</label>
      <input type="password" v-model="password" required />
      <label>Role:</label>
      <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer">Web Designer</option>
      </select>
      <label>Skills (press alt + comma to add):</label>
      <!-- IMPORTANT: because the keboard event modifier "alt"
      doens´t work, I remove it. That modifier is important,
      check it out way in prvious branch. -->
      <input type="text" v-model="tempSkill" @keyup="addSkill" />
      <div v-for="skill in skills" :key="skill" class="pill">
        <!-- 1) Add on click event calling the function deleteSkill,
        passing the skill as an argument. Remember, that as we
        used the v-for loop, skill is the current skill.-->
        <span @click="deleteSkill(skill)">{{ skill }}</span>
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
      tempSkill: "",
      skills: [],
    };
  },
  methods: {
    addSkill($event) {
      if ($event.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkill = "";
      }
    },
    /* 2) Create the deleteSkill functiona and accept skill
    as parameter.  */
    deleteSkill(skill) {
      /* 3) Update the skills array to an array without the value
      we want to delete. To do that, assign the skills array to the 
      filter method. The filter method cycle through an array and
      fires a function for each item in the array. If we return true
      for an item in the array, we keep it in the array. If we return
      false, we remove it from the array. */
      this.skills = this.skills.filter((item) => {
        /* 4) I have to return false so that I can remove the clicked 
        skill from the array. In other words, if the item equals the skill, 
        I want to return false. So, I say, return skill is not equal to
        item (return skill !== item;) */
        return skill !== item;
      });
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
</style>
