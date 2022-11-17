<template>
  <div>
    <BaseCheckbox :title="item.title" v-model="model.checked" />
    <ul v-if="item.categories">
      <li v-for="(category, idx) in item.categories" :key="idx">
        <CheckboxItem :item="category" />
      </li>
    </ul>
  </div>
</template>

<script>
import BaseCheckbox from "./BaseCheckbox";
export default {
  name: "CheckboxItem",
  components: {
    BaseCheckbox,
  },
  props: {
    item: Object,
  },

  methods: {
    // handleChange(e) {
    //   this.$emit("change", e);
    // },
  },
  computed: {
    model: {
      get() {
        console.log("get1", this.item.title, this.item.checked);
        return this.item;
      },
      set(value) {
        console.log("set", value);
        this.$emit("input", value);
      },
    },
  },
};
</script>
