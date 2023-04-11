<template>
  <div class="header__wrapper">
    <div class="header__sections">
      <router-link :to="{ name: 'home' }" class="section" id="logo-section">
        <long-logo class="header__logo" colour="#010101" />
      </router-link>

      <div class="section" id="nav-section">
        <header-nav />
      </div>

      <div class="section" id="cta-section">
        <header-ctas />
      </div>
    </div>
  </div>
</template>

<script>
import longLogo from "@/assets/logo/long-logo.vue";
import headerNav from "@/components/home/header/header-nav.vue";
import headerCtas from "@/components/home/header/header-ctas.vue";

export default {
  name: "home-header",
  components: {
    longLogo,
    headerNav,
    headerCtas,
  },
};
</script>

<style scoped>
.header__wrapper {
  width: 100%;
  max-width: 1400px;
  margin-inline: auto;
}

.header__sections {
  display: grid;
  align-items: center;
  grid-template-columns: auto 1fr 1fr;
  grid-gap: 40px;
  gap: 40px;
  margin-block: 25px 0;
  margin-inline: 20px;
}

.header__logo {
  height: 30px;
}
</style>
