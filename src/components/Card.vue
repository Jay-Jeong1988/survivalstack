<template>
  <div class="gear">
    <router-link :to="`/gears/${item.name}`">
      <b-card
        style="
            white-space: nowrap;
            border-radius: 10px;
            font-family: 'Fredericka the Great';
             text-shadow: 1px 1px 0 rgba(0, 0, 0, 0.35);
             "
        no-body
        text-variant="white"
        :bg-variant="displayCardBg"
      >
        <b-card-img
          style="
            filter: contrast(0.5);
            max-height: 180px;
            border-radius: 10px;
            border-bottom-left-radius: 0;
            border-bottom-right-radius: 0;
            "
          :src="`${item.pictureUrl}`"
          alt="item image"
        ></b-card-img>
        <b-card-header style="display: flex; justify-content: space-between; align-items: center; overflow: scroll; padding: .5rem 1.25rem">
          <div
            class="headerIcons"
            style="display: flex; justify-content: space-between; min-width: 4em;"
          >
            <span class="categoryIcon">
              <img :src="iconSource" />
            </span>
            <span class="checkIcon">
              <button @click="toggleCheckIcon">
                <img :src="`./img/icons/${displayCheckIcon}.svg`" />
              </button>
            </span>
          </div>
          <div class="buffer"></div>
          <h1>{{item.name[0].toUpperCase() + item.name.slice(1)}}</h1>
        </b-card-header>
      </b-card>
    </router-link>
  </div>
</template>
<script>
// import {api} from '../api'
export default {
  name: "Card",
  props: ["item"],
  data() {
    return {
      iconSource: `./img/icons/${this.item.category}.svg`
    };
  },
  created() {},
  computed: {
    displayCheckIcon() {
      return this.item.checked ? "checked" : "unchecked";
    },
    displayCardBg() {
      return this.item.default ? "dark" : "secondary";
    }
  },
  methods: {
    toggleCheckIcon(e) {
      e.preventDefault();
      this.item.checked = !this.item.checked;
    }
  }
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Fredericka+the+Great&display=swap");
.gear a {
  cursor: initial;
}
.headerIcons img {
  width: 1.8em;
}
.card-header h1 {
  margin-bottom: 0;
}
.buffer {
  min-width: 1em;
}
.headerIcons button {
  background-color: transparent;
  border: none;
}
</style>