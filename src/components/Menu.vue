<template>
  <div id="menu">
    <div class="fixedContainer">
      <div class="logo">
        <router-link to="/">
          <img src="../assets/images/survivalstack.png" />
        </router-link>
      </div>
      <div class="filters">
        <button class="category">
          <img src="../assets/images/category.svg" />
          <p>Category</p>
        </button>
        <button class="alphabet">
          <img src="../assets/images/alphabet.svg" />
          <p>Alphabetical</p>
        </button>
        <button class="checked">
          <img src="../assets/images/checked.svg" />
          <p>Ready</p>
        </button>
        <button class="news">
          <img src="../assets/images/news.svg" />
          <p>News & Events</p>
        </button>
        <button class="skills">
          <img src="../assets/images/skills.svg" />
          <p>Skills</p>
        </button>
        <button class="hunting">
          <img src="../assets/images/hunting.svg" />
          <p>Hunting</p>
        </button>
        <button class="trips">
          <img src="../assets/images/trips.svg" />
          <p>Trips</p>
        </button>
        <button class="community">
          <img src="../assets/images/community.svg" />
          <p>Community</p>
        </button>
      </div>
      <div class="footer"></div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Menu",
  data() {
    return {
      categories: []
    };
  },
  computed: {},
  methods: {
    // closeMenubar () {
    //     this.$emit("closeMenubar")
    // },
    // logout () {
    //     this.$emit("logout")
    // },
    // redirectTo(path) {
    //     this.$emit("closeMenubar")
    //     this.$router.push(path)
    // }
  },
  created() {},
  props: []
};
</script>
<style scoped>
#menu {
  min-width: 16em;
  border-right: solid 1px rgb(211, 211, 211);
}
@media only screen and (max-width: 924px) {
  #menu {
    display: none;
  }
}
button {
  border: none;
  background-color: transparent;
}

.nav-menu:last-of-type {
  margin-bottom: 4em;
}
.fixedContainer {
  width: calc(16em - 1px);
  height: 100vh;
  position: fixed;
  top: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #0d1822;
}
.closeMenu {
  margin-bottom: 4em;
}
.closeMenu button img {
  width: 1em;
}
.closeMenu * {
  display: inline-block;
}
.logo img {
  width: 10em;
}
.filters img {
  width: 1.7em;
}
.filters p {
  margin-top: 0.5em;
  color: white;
  font-size: 0.8em;
}
.filters {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-auto-rows: 7rem;
  width: inherit;
}
</style>