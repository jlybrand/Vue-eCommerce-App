<template>
  <nav class="navbar navbar-expand-lg bg-light">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">Vue Shop</router-link>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <router-link to="/" class="nav-link">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/products" class="nav-link" href="#"
              >Products</router-link
            >
          </li>
          <li class="nav-item">
            <router-link to="/about" class="nav-link" href="#"
              >About</router-link
            >
          </li>
          <li class="nav-item">
            <a @click="toggleLogin" class="btn btn-outline-succes">Log In</a>
          </li>
           <li class="nav-item">
            <a @click="toggleSignup" class="btn btn-outline-succes">Sign Up</a>
          </li>
        </ul>
        <form class="d-flex" role="search">
          <input
            class="form-control me-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
          />
          <button class="btn btn-outline-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>
  <Login @close="toggleLogin" :loginActive="loginActive"></Login>
  <Signup  @close="toggleSignup" :signupActive="signupActive"></Signup>
</template>

<script>
import Login from "./Login.vue";
import Signup from "./Signup.vue";
import { ref } from "vue";

export default {
  name: "NavBar",
  props: {
    msg: String,
  },
  components: {
    Login,
    Signup
  },

  setup() {
    const loginActive = ref(false);
    const signupActive = ref(false);
    const toggleLogin = () => {
      loginActive.value = !loginActive.value;
    };
    const toggleSignup = () => {
      signupActive.value = !signupActive.value;
    };
    return { loginActive, toggleLogin, signupActive, toggleSignup  };
  },
  
};
</script>

<style scoped>
.navbar-brand {
  color: purple;
}
.nav-link {
  color: #444;
}

@media (min-width: 992px) {
  .navbar.custom-nav {
    padding-top: 16px;
    padding-bottom: 16px;
    background-color: #fff !important;
  }
}
</style>
