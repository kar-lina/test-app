<template>
  <div>
    <input type="checkbox" v-model="model" :checked="checked" />
    <label for="title">{{ title }}</label>
  </div>
</template>

<script>
export default {
  name: "BaseCheckbox",
  props: {
    title: String,
    checked: Boolean,
  },
  methods: {
    handleChange() {
      this.checkedVal = !this.checkedVal;

      this.$emit("change", this.checkedVal);
    },
  },
  computed: {
    model: {
      get() {
        console.log("get");
        return this.checked;
      },
      set(value) {
        console.log("set", value);
        this.$emit("input", value);
      },
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
