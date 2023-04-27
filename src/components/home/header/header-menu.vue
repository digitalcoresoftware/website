<template>
  <div class="menu__btn">
    <div class="menu__wrapper">
      <menu-icon class="menu__bars" colour="#010101" />
    </div>
  </div>
</template>

<script>
import menuIcon from "@/assets/icons/menu-icon.vue";
export default {
  name: "header-menu",
  components: {
    menuIcon,
  },
};
</script>

<style scoped>
.menu__btn {
  width: 45px;
  height: 35px;
  border-radius: 5px;
  border: 1px solid var(--second-col);
}

.menu__wrapper {
  height: 100%;
  display: flex;
  justify-content: center;
}

.menu__bars {
  width: 25px;
}
</style>
