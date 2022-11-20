<template>
  <div id="app">
    <div class="container">
      <ul>
        <li v-for="(item, idx) in items" :key="idx">
          <CheckboxCategory @change="handleChange($event, idx)" :item="item" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import CheckboxCategory from "./components/CheckboxCategory";
export default {
  name: "App",
  components: {
    CheckboxCategory,
  },
  data() {
    return {
      items: [
        {
          title: "title",
          checked: false,
          categories: [
            { title: "title", checked: false },
            { title: "title", checked: false },
            { title: "title", checked: false },
            {
              title: "title",
              checked: false,
              categories: [
                { title: "title_true", checked: true },
                { title: "title", checked: false },
                { title: "title", checked: false },
                { title: "title", checked: false },
                {
                  title: "title",
                  checked: false,
                  categories: [
                    { title: "title", checked: false },
                    { title: "title", checked: false },
                    { title: "title", checked: false },
                  ],
                },
              ],
            },
          ],
        },
        {
          title: "title",
          checked: false,
          categories: [
            { title: "title", checked: false },
            { title: "title", checked: false },
            { title: "title", checked: false },
            { title: "title", checked: false },
          ],
        },
      ],
    };
  },
  methods: {
    handleChange(e, idx) {
      this.items[idx] = e;
    },
  },

  watch: {
    items() {
      console.log("changed");
    },
  },
};
</script>

<style>
#app {
  padding: 10rem;
}
</style>
