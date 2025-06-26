<template>
  <div class="login-container">
    <h2>Đăng nhập</h2>
    <form @submit.prevent="login">
      <div>
        <label class="form-label" for="username">Tên đăng nhập</label>
        <input v-model="username" id="username" type="text" class="form-control" required />
      </div>
      <div>
        <label class="form-label" for="password">Mật khẩu</label>
        <input v-model="password" id="password" type="password" class="form-control" required />
      </div>
      <button class="btn btn-primary mt-2" type="submit">Đăng nhập</button>
      <p v-if="error" class="text-danger mt-2">{{ error }}</p>
    </form>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      username: "",
      password: "",
      error: "",
    };
  },
  methods: {
    login() {
      if (this.username === "admin" && this.password === "admin") {
        localStorage.setItem("token", "fake-token");
        this.$router.push({ name: "contactbook" });
      } else {
        this.error = "Sai tên đăng nhập hoặc mật khẩu.";
      }
    },
  },
};
</script>