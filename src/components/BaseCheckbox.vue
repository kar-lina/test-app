<template>
  <div>
    <input
      ref="checkbox"
      type="checkbox"
      :checked="checked"
      @change="$emit('change', $event.target.checked)"
      :indeterminate.prop="indeterminate"
    />
    <label for="title">{{ title }}</label>
  </div>
</template>

<script>
export default {
  name: "BaseCheckbox",

  model: {
    prop: "checked",
    event: "change",
  },
  props: {
    title: String,
    checked: Boolean,
    indeterminate: Boolean,
  },
  data() {
    return {};
  },
  methods: {},
  computed: {},
  watch: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
