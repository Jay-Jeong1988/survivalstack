<template>
  <div id="app">
    <Menu :class="{showMenu: isMenu}" :currentPage="currentPage"></Menu>
    <div id="main">
      <Navbar :totalItemCount="totalItemCount" :checkedItemCount="checkedItemCount"></Navbar>
      <router-view :customItems="customItems" :defaultItems="defaultItems" :currentPage="currentPage"/>
      <div class="showMenuBtn" @click="toggleMenu">
        <p>Show filters</p>
      </div>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import BootstrapVue from "bootstrap-vue";
import Menu from "./components/Menu.vue";
import Navbar from "./components/Navbar.vue";
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
Vue.use(BootstrapVue);
export default {
  name: "App",
  components: { Menu, Navbar },
  data() {
    return {
      currentPage: "gear list",
      isMenu: false,
      user: null,
      customItems: [
        {
          name: "jerky",
          default: false,
          category: "food",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/jerky-creamy50.jpg",
          checked: false
        },
        {
          name: "passport",
          default: false,
          category: "personal",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/passport-creamy50.jpg",
          checked: false
        },
        {
          name: "tent",
          default: false,
          category: "shelter",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/tent-creamy50.jpg",
          checked: false
        },
        {
          name: "sleeping bag",
          default: false,
          category: "shelter",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024,fo-bottom/sleeping-bag-creamy50.jpg",
          checked: false
        }
      ],
      defaultItems: [
        {
          name: "knife",
          default: true,
          category: "tool",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/knife-creamy50.jpg",
          checked: true
        },
        {
          name: "backpack",
          default: true,
          category: "carrier",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024,cm-resize/backpack-creamy50.jpg",
          checked: false
        },
        {
          name: "flashlight",
          default: true,
          category: "tool",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024,cm-resize/flashlight-creamy50.jpg",
          checked: false
        },
        {
          name: "compass",
          default: true,
          category: "tool",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024,cm-resize/compass-creamy50.jpg",
          checked: false
        },
        {
          name: "watch",
          default: true,
          category: "tool",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024,cm-resize/watch-creamy50.jpg",
          checked: false
        },
        {
          name: "magnesium fire starter",
          default: true,
          category: "tool",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/magnesium-fire-starter-creamy50.jpg",
          checked: false
        },
        {
          name: "lighter",
          default: true,
          category: "tool",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/lighter-creamy50.jpg",
          checked: false
        },
        {
          name: "nutrition bar",
          default: true,
          category: "food",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/nutrition-bar-creamy50.jpg",
          checked: false
        },
        {
          name: "gloves",
          default: true,
          category: "protection",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/gloves-creamy50.jpg",
          checked: false
        },
        {
          name: "shoes",
          default: true,
          category: "protection",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/shoes-creamy50.jpg",
          checked: false
        },
        {
          name: "jacket",
          default: true,
          category: "protection",
          thumbnailUrl:
            "https://ik.imagekit.io/kitkitkitit/survivalstack/tr:q-100,ar-6-4,w-1000e-usm-2-2-0.8-0.024/jacket-creamy50.jpg",
          checked: false
        }
      ]
    };
  },
  computed: {
    totalItemCount() {
      return this.customItems.length + this.defaultItems.length;
    },
    checkedItemCount() {
      var defaultCheckedItems = 0;
      var customCheckedItems = 0;
      this.defaultItems.forEach(item => {
        if (item.checked) defaultCheckedItems++;
      });
      this.customItems.forEach(item => {
        if (item.checked) customCheckedItems++;
      });
      return defaultCheckedItems + customCheckedItems;
    }
  },
  methods: {
    toggleMenu() {
      this.isMenu = !this.isMenu;
    },
    logout() {
      localStorage.removeItem("user");
      this.user = null;
      this.closeMenubar();
      this.$router.push("/login");
    },
    login(user) {
      localStorage.setItem("user", JSON.stringify(user));
      this.user = user;
      this.$router.push("/");
    }
  },
  created() {
    
  }
};
</script>

<style>
a:hover {
  text-decoration-line: none;
}
#app {
  display: flex;
  overflow-x: hidden;
  min-height: 100vh;
  background-color: #fff;
}
#main {
  background-image: url(
    http://ik.imagekit.io/kitkitkitit/tr:q-100,ar-4-6,w-1000/campfire.jpg
  );
}
.showMenuBtn {
  position: fixed;
  z-index: 1001;
  bottom: 0;
  display: none;
  color: white;
  background-color: #f78410;
  width: 100vw;
  height: 3.5em;
  text-align: center;
  vertical-align: center;
}
.showMenuBtn p {
  margin: 0;
}
@media only screen and (max-width: 600px) {
  #main {
    background-position: bottom;
  }
}
@media only screen and (max-width: 924px) {
  .showMenuBtn {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  #menu.showMenu {
    display: block;
    position: fixed;
    z-index: 1000;
  }
  #menu.showMenu .fixedContainer {
    width: 100vw;
  }
}
</style>