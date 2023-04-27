<template>
  <div class="header__wrapper">
    <div class="header__sections">
      <router-link :to="{ name: 'home' }" id="long-logo">
        <long-logo class="header__logo" colour="#010101" />
      </router-link>

      <router-link :to="{ name: 'home' }" id="icon-logo">
        <icon-logo class="header__logo" colour="#010101" />
      </router-link>

      <div id="nav-section">
        <header-nav />
      </div>

      <div id="cta-section">
        <header-ctas />
      </div>
    </div>
  </div>
</template>

<script>
import longLogo from "@/assets/logo/long-logo.vue";
import iconLogo from "@/assets/logo/icon-logo.vue";
import headerNav from "@/components/home/header/header-nav.vue";
import headerCtas from "@/components/home/header/header-ctas.vue";

export default {
  name: "home-header",
  components: {
    longLogo,
    iconLogo,
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

#icon-logo {
  display: none;
}

@media screen and (max-width: 910px) {
  #long-logo {
    display: none;
  }

  #icon-logo {
    display: block;
  }

  .header__logo {
    height: 35px;
  }

  .header__sections {
    grid-gap: 20px;
    gap: 20px;
  }
}

@media screen and (max-width: 730px) {
  #nav-section {
    display: none;
  }

  .header__sections {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
}
</style>
