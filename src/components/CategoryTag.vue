/* eslint-disable */
<template>
  <label class="typo__label">Filter by Tags</label>
  <multiselect
    class="text-white bg-success p-0 rounded mb-1"
    v-model="localSelectedTags"
    :options="tagOptions"
    :option-height="104"
    :multiple="true"
    placeholder="Search or add a tag"
    @change="updateSelectedTags"
    :style="{ '--multiselect-input-width': '150px' }"
  ></multiselect>

  <!-- <div>
  <form action="/action_page.php">
      <input
        class="form-check-input"
        type="checkbox"
        id="category1"
        name="category1"
        value="Clothing"
        v-model="selectedTags"
        @change="updateSelectedTags"
      />
      <label for="category1" class="text-white bg-success p-0 rounded mb-1">
        Clothing</label
      ><br />
      <input
        class="form-check-input"
        @change="updateSelectedTags"
        type="checkbox"
        id="category2"
        v-model="selectedTags"
        name="category2"
        value="Food & Beverage"
      />
      <label for="category2" class="text-white bg-success p-0 rounded mb-1">
        Food & Beverage</label
      ><br />
      <input
        class="form-check-input"
        @change="updateSelectedTags"
        type="checkbox"
        id="category3"
        v-model="selectedTags"
        name="category3"
        value="Supplements"
      />
      <label for="vehicle3" class="text-white bg-success p-0 rounded mb-1">
        Supplements</label
      ><br /><br />
    </form>
  </div>-->
</template>

<script>
import Multiselect from "vue-multiselect";
export default {
  components: { Multiselect },
  props: {
    selectedTags: Array,
  },

  data() {
    return {
      tagOptions: ["Clothing", "Food & Beverage", "Supplements"],
    };
  },
  computed: {
    localSelectedTags: {
      get() {
        return this.selectedTags;
      },
      set(newValue) {
        this.$emit("update:selectedTags", newValue);
      },
    },
  },
  methods: {
    updateSelectedTags() {
      this.$emit("update:selected-tags", this.localSelectedTags);
    },
  },
};
</script>
