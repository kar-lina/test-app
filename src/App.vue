<template>
  <div id="app">
    <div class="container">
      <ul>
        <li v-for="item in items" :key="item.idx">
          <CheckboxItem :item="item" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import CheckboxItem from "./components/CheckboxItem";
export default {
  name: "App",
  components: {
    CheckboxItem,
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
};
</script>

<style>
#app {
  padding: 10rem;
}
</style>
