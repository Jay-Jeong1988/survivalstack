<template>
  <div class="navbar">
    <a id="homeLink" href>
      <img src="../assets/images/bonfire.svg" />
    </a>
    <DigitalClock></DigitalClock>
    <div class="rightSideContainer">
      <span id="progress">
        <p>GEAR STACK&nbsp;</p>
        <p>&nbsp;{{pad}}/</p>
        <p>{{totalItemCount}}</p>
      </span>
      <a id="twitter" href>
        <img src="../assets/images/twitter.svg" />
      </a>
    </div>
  </div>
</template>
<script>
import DigitalClock from "./DigitalClock";

export default {
  name: "Navbar",
  data() {
    return {};
  },
  components: {
    DigitalClock
  },
  computed: {
    pad() {
      var s = this.checkedItemCount + "";
      var size = `${this.totalItemCount}`.length;
      while (s.length < size) s = "0" + s;
      return s;
    }
  },
  methods: {},
  created() {},
  props: ["totalItemCount", "checkedItemCount"]
};
</script>
<style scoped>
.navbar {
  background: #0f3854;
  background-size: 100%;
  width: calc(100vw - 16em - 1px);
  height: 4em;
  background-color: #0d1822;
  display: flex;
  justify-content: space-between;
  position: fixed;
  top: 0;
  z-index: 1;
  border-bottom: 1px solid rgb(211, 211, 211);
  color: white;
  padding: 0.5rem 1.5rem;
  white-space: nowrap;
  flex-wrap: nowrap;
  overflow: hidden;
}
@media only screen and (max-width: 924px) {
  .navbar {
    width: 100vw;
  }
}
.nav-menu button {
  background-color: transparent;
  border: none;
}
.rightSideContainer {
  display: flex;
  align-items: center;
}
#twitter {
    margin-left: 1em;
}
#twitter > img {
  width: 1.8em;
}
#progress > p {
  display: contents;
}
#progress * {
  font-family: "Share Tech Mono", monospace;
  text-align: center;
  color: #daf6ff;
  text-shadow: 0 0 20px rgb(230, 143, 85), 0 0 20px rgba(10, 175, 230, 0);
  letter-spacing: 0.05em;
  padding: 5px 0;
  font-size: 24px;
}
#homeLink {
  display: none;
}
#homeLink > img {
  width: 2.5em;
}
@media only screen and (max-width: 924px) {
  #homeLink {
    display: block;
  }
  #progress * {
    font-size: 18px;
  }
}
</style>