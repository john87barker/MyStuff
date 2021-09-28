<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark pl-3 container-fluid">
    <div class="row">
      <router-link class="navbar-brand col-md-3" :to="{ name: 'Home' }">
        <div class="flex-column align-items-center">
          <img
            alt="logo"
            src="../assets/img/cw-logo.png"
            height="45"
          />
        </div>
      </router-link>
      <div class="text-light col-md-6">
        <h1>
          MyStuf
        </h1>
      </div>
    </div>
  </nav>
</template>

<script>
import { AuthService } from '../services/AuthService'
import { AppState } from '../AppState'
import { computed, reactive } from 'vue'
export default {
  setup() {
    const state = reactive({
      dropOpen: false
    })
    return {
      state,
      user: computed(() => AppState.user),
      async login() {
        AuthService.loginWithPopup()
      },
      async logout() {
        AuthService.logout({ returnTo: window.location.origin })
      }
    }
  }
}
</script>

<style scoped>
.dropdown-menu {
  user-select: none;
  display: block;
  transform: scale(0);
  transition: all 0.15s linear;
}
.dropdown-menu.show {
  transform: scale(1);
}
.hoverable {
  cursor: pointer;
}
a:hover {
  text-decoration: none;
}
.nav-link{
  text-transform: uppercase;
}
.navbar-nav .router-link-exact-active{
  border-bottom: 2px solid var(--bs-success);
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
}
</style>
