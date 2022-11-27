
<template>
  <div class="login">
      <h1>Login</h1>
      <form action="/auth" method="post">
          <label for="username">
              <!-- font awesome icon -->
              <i class="fas fa-user"></i>
          </label>
          <input type="text" name="username" placeholder="Username" id="username" required>
          <label for="password">
              <i class="fas fa-lock"></i>
          </label>
          <input type="password" name="password" placeholder="Password" id="password" required>
          <input type="submit" value="Login">
      </form>
  </div>
</template>
<style src="../src/assets/login.css"></style>

<script>
 import { Form, Field, ErrorMessage } from 'vee-validate';
 import * as yup from 'yup';
  export default {
name: "Login",
components: {
  Form,
  Field,
  ErrorMessage,
},
data() {
  const schema = yup.object().shape({
    username: yup.string().required("Username is required!"),
    password: yup.string().required("Password is required!"),
  });

  return {
    loading: false,
    message: "",
    schema,
  };
},
computed: {
  loggedIn() {
    return this.loggedIn;
  },
},
created() {
  if (this.loggedIn) {
    this.$router.push("/profile");
  }
},
methods: {
  handleLogin(user) {
    this.loading = true;

    this.$store.dispatch("auth/login", user).then(
      () => {
        this.$router.push("/profile");
      },
      (error) => {
        this.loading = false;
        this.message =
          (error.response &&
            error.response.data &&
            error.response.data.message) ||
          error.message ||
          error.toString();
      }
    );
  },
},
};

</script>

