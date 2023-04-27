<template>
  <div class="header__cta__wrapper">
    <div class="header__cta__container" id="search-cta">
      <app-search />
    </div>

    <router-link
      :to="{ name: 'home' }"
      class="header__cta__container"
      id="auth-cta"
    >
      <div class="cta__wrapper">
        <span class="cta__txt">Sign Up</span>
      </div>
    </router-link>

    <header-menu id="menu-btn" />
  </div>
</template>

<script>
import appSearch from "@/components/global/app-search.vue";
import headerMenu from "@/components/home/header/header-menu.vue";

export default {
  name: "header-ctas",
  components: {
    appSearch,
    headerMenu,
  },
};
</script>

<style scoped>
.header__cta__wrapper {
  width: fit-content;
  margin-inline-start: auto;
  display: grid;
  grid-template-columns: repeat(2, max-content);
  grid-gap: 10px;
  gap: 10px;
}

.header__cta__container {
  height: 35px;
  display: flex;
  align-items: center;
  text-align: center;
  position: relative;
  background: var(--second-col);
}

.cta__wrapper {
  color: var(--sub-font-col);
}

.cta__txt {
  padding-inline: 15px;
}

/* Auth Cta */
#auth-cta {
  cursor: pointer;
  border-radius: 25px;
}

#auth-cta > .cta__wrapper {
  color: var(--font-col);
}

/* Search */
#search-cta {
  border-radius: 10px;
  position: relative;
}

#menu-btn {
  display: none;
}

@media screen and (max-width: 730px) {
  #auth-cta {
    display: none;
  }

  #menu-btn {
    display: block;
  }

  .header__cta__wrapper {
    grid-template-columns: auto 1fr;
  }
}
</style>
