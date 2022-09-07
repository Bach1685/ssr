// no-prefetch - не загружает страницу, если пользователь не на ней

<template>
  <nav class="navbar navbar-expand-lg bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Navbar</a>

      <div class="collapse navbar-collapse">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <nuxt-link
              active-class="active"
              exact
              no-prefetch
              class="nav-link"
              aria-current="page"
              to="/"
            >
              Home
            </nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link
              no-prefetch
              active-class="active"
              class="nav-link"
              to="/about"
            >
              About
            </nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link
              no-prefetch
              active-class="active"
              class="nav-link"
              to="/users"
            >
              Users
            </nuxt-link>
          </li>
          <li class="nav-item" v-if="!hasToken">
            <nuxt-link
              no-prefetch
              active-class="active"
              class="nav-link"
              to="/login"
            >
              Login
            </nuxt-link>
          </li>

          <li v-else class="nav-item">
            <a @click.prevent="logout" class="nav-link"> Logout </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$store.dispatch("logout");
      this.$route.push("/login");
    },
  },
  computed: {
    hasToken() {
      return this.$store.getters.hasToken;
    },
  },
};
</script>

