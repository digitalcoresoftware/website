<template>
  <div class="header__link__wrapper">
    <div class="header__link__btn" id="app-btn">
      <div class="link__wrapper">
        <span>Apps</span>
      </div>
    </div>

    <div class="header__link__btn" id="about-btn">
      <div class="link__wrapper">
        <span>About</span>
      </div>
    </div>

    <div class="header__link__btn" id="contact-btn">
      <div class="link__wrapper">
        <span>Contact</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "header-nav",
};
</script>

<style scoped>
.header__link__wrapper {
  display: grid;
  grid-template-columns: repeat(3, max-content);
  grid-gap: 5px;
  gap: 5px;
}

.header__link__btn {
  height: 35px;
  display: flex;
  align-items: center;
  text-align: center;
  position: relative;
  cursor: pointer;
}

.link__wrapper {
  color: var(--sub-font-col);
  padding-inline: 15px;
}

.link__wrapper:hover {
  color: var(--font-col);
}

.link__wrapper {
  width: 100%;
  text-align: center;
}

/* Apps Btn */
#app-btn:hover {
  background: var(--second-col);
  border-radius: 25px;
}

#app-btn:hover > .link__wrapper {
  color: var(--font-col);
}

/* About Btn */
#about-btn:hover {
  background: var(--second-col);
  border-radius: 25px;
}

#about-btn:hover > .link__wrapper {
  color: var(--font-col);
}

/* Contact Btn */
#contact-btn:hover {
  background: var(--second-col);
  border-radius: 25px;
}

#contact-btn:hover > .link__wrapper {
  color: var(--font-col);
}
</style>
