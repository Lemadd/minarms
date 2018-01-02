<template>
   <div id="app">
    <section class="hero is-large">
      <div class="hero-head">
          <header class="navbar">
            <div class="container">
              <div class="navbar-brand">
                <a class="navbar-item" href="/">
                  <img src="./assets/logo.png">
                </a>
                <span class="navbar-burger burger" data-target="navbarMenuHeroA">
                  <span></span>
                  <span></span>
                  <span></span>
                </span>
              </div>
                <router-link :to="{ name: 'Home' }" class="navbar-item">Home</router-link>
                <router-link to="/about" class="navbar-item">About</router-link>
                <router-link to="/coins/ethereum" class="navbar-item">Ethereum</router-link>
                <router-link to="/coins/bitcoin" class="navbar-item">Bitcoin</router-link>
            </div>
          </header>
        </div>
      <router-view>
    </router-view>
  </section>
  </div>

</template>

<script>
export default {
  name: 'app'
}
</script>