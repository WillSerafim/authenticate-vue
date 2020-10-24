<template>
  <nav class="navbar navbar-expand-lg navbar-bytebank">
      <a class="navbar-brand" href="#">Inter Bank</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <NavBarLogin v-if="userLoggedIn"/>
        <NavBarLogout v-else />

      </div>
    </nav>
</template>

<script>
import NavBarLogin from '@/components/NavBarLogin'
import NavBarLogout from '@/components/NavBarLogout'
export default {
  name: 'NavBar',
  components: {
    NavBarLogin,
    NavBarLogout
  },
  computed: {
    userLoggedIn() {
      return Boolean(localStorage.getItem('token'));
    }
  },
}
</script>

<style>
.navbar {
  background: linear-gradient(81deg,#ff500f,#ff8700);
}
.navbar-bytebank a {
  color: #fff;
}
.navbar-bytebank a:hover {
  color: rgb(110, 94, 94);
}
</style>