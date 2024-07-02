<template>
  <header id="main">
    <nav>
      <Logo />
      <NavLinks />
    </nav>
  </header>
</template>

<script>
import Logo from './Logo.vue';
// import Requisites from './Requisites.vue';
import NavLinks from './NavLinks.vue';

export default {
  components: {
    Logo,
    // Requisites,
    NavLinks
  }
};
</script>
<style scoped>
</style>
