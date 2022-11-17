<template>
  <div id="app">
    <div class="container">
      <ul>
        <li v-for="item in items" :key="item.idx">
          <CheckBox :item="item" msg="Welcome to Your Vue.js App" />
        </li>
      </ul>
      <CheckBox msg="Welcome to Your Vue.js App" />
    </div>
  </div>
</template>

<script>
import CheckBox from "./components/CheckBox.vue";

export default {
  name: "App",
  components: {
    CheckBox,
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
                { title: "title", checked: true },
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
};
</script>

<style>
#app {
  padding: 10rem;
}
</style>
