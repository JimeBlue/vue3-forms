<template>
  <!-- The net ninja github branch: lessson44 -->
  <!-- (https://github.com/iamshaunjp/Vue-3-Firebase/blob/lesson-44/web-forms/src/App.vue) -->

  <div>
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
      <!-- EXPLANATION: there are 2 ways of tracking values of checked checkboxes -->
      <!-- WAY ONE - SINGLE CHECKBOX-->
      <!-- 1) Add the checkboxes -->
      <div class="terms">
        <!-- 2) Track the value of the checked checkbox setting the value
        of v-model to "terms". The property terms is a boolean. -->
        <input type="checkbox" v-model="terms" required />
        <label>Accept terms and conditions</label>
      </div>
      <!-- WAY TWO - MULTIPLE CHECKBOXES -->
      <div>
        <!-- A) Create the checkboxes. Add a value to each of them.
        Set the v-model of all of them to names. 
        The names property is an array -->
        <input type="checkbox" value="Fede" v-model="names" />
        <label>Fede</label>
        <input type="checkbox" value="Ariel" v-model="names" />
        <label>Ariel</label>
        <input type="checkbox" value="Jimena" v-model="names" />
        <label>Jimena</label>
      </div>
    </form>
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <!-- 4) Ouput the value of terms just to see it´s a boolean -->
    <p>Terms accepted: {{ terms }}</p>
    <!-- C) Output the checked value. Use v-for ´cause it´s an array -->
    <ul>
      Selected names
      <li v-for="name in names">{{ name }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "designer",
      /* 3) Create the property terms to store the value of the 
      checked checkbox and set it to false. If I want the checkbox
      to be initially checked by dafault, I set term to true*/
      terms: false,
      /* B) Create the names property to store the value of
      the checked checkboxes and set it to an empty array. */
      names: [],
    };
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
