<template>
  <div>
    <form>
      <label>Email:</label>
      <!-- 1) Track value of email and password input
      using data binding with the v-model directive -->
      <input type="email" v-model="email" required />
      <label>Password:</label>
      <input type="password" v-model="password" required />
    </form>
    <!-- 3)Optional step: output values entered into
    email and password inputs -->
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      /* 2) Add the email and password properties to store
        the value of those inputs */
      email: "",
      password: "",
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
</style>
