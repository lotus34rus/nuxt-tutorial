<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <!-- <div class="container"> -->
    <a class="navbar-brand" href="#">Nuxt SSR</a>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item">
          <nuxt-link exact no-prefetch active-class='active' to="/" class="nav-link">
                Home
          </nuxt-link>
        </li>
        <li class="nav-item">
           <nuxt-link active-class='active' to="/about" class="nav-link">
                About
          </nuxt-link>
        </li>
        <li class="nav-item">
           <nuxt-link active-class='active' to="/users" class="nav-link">
                Users
          </nuxt-link>
        </li>

        <li class="nav-item" v-if="!hasToken">
           <nuxt-link active-class='active' to="/login" class="nav-link">
                Login
          </nuxt-link>
        </li>
         <li class="nav-item" v-else>
           <a class="nav-link" @click.prevent="logout">
                Logout
          </a>
        </li>
      </ul>
    </div>
    <!-- </div> -->
  </nav>
</template>


<script>
export default {
  computed: {
    hasToken(){
      return this.$store.getters.hasToken
    }
  },
  methods: {
    logout(){
      this.$store.dispatch('logout')
      this.$router.push('/login')
    }
  },
}
</script>