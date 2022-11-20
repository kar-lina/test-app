<template>
  <div>
    <BaseCheckbox
      :checked="item.checked"
      :indeterminate="!hasAllCategoriesChecked && hasSomeCategoriesChecked"
      :title="item.title"
      @change="handleItemChange"
    />
    <ul v-if="item.categories">
      <li v-for="(category, idx) in item.categories" :key="idx">
        <CheckboxCategory
          @change="handleCategoryChange($event, idx)"
          :item="category"
        />
      </li>
    </ul>
  </div>
</template>

<script>
import BaseCheckbox from "./BaseCheckbox";
export default {
  name: "CheckboxCategory",
  components: {
    BaseCheckbox,
  },
  props: {
    item: Object,
  },
  data() {
    return {
      localItem: {},
    };
  },
  mounted() {
    this.localItem = Object.assign(this.item);
  },

  methods: {
    handleItemChange(e) {
      e
        ? this.checkAllCategories(this.localItem)
        : this.uncheckAllCategories(this.localItem);
      this.localItem.checked = e;
      this.$emit("change", this.localItem);
    },
    handleCategoryChange(e, idx) {
      this.localItem.categories[idx] = e;
      this.localItem.checked = this.hasAllCategoriesChecked;

      this.$emit("change", this.localItem);
    },

    checkAllCategories(item) {
      if (item.categories?.length) {
        for (let c of item.categories) {
          c.checked = true;
          if (c.categories?.length) {
            this.checkAllCategories(c);
          }
        }
      }
    },
    uncheckAllCategories(item) {
      if (item.categories?.length) {
        for (let c of item.categories) {
          c.checked = false;
          if (c.categories?.length) {
            this.uncheckAllCategories(c);
          }
        }
      }
    },
  },
  computed: {
    checkedCategories() {
      return this.localItem.categories?.filter((c) => c.checked)?.length ?? 0;
    },
    hasAllCategoriesChecked() {
      return this.checkedCategories === this.item.categories?.length;
    },
    hasSomeCategoriesChecked() {
      return (
        this.checkedCategories > 0 &&
        this.checkedCategories < this.item.categories?.length
      );
    },
  },
};
</script>
