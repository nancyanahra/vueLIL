<template>
  <div>
    <!-- <multiselect
      v-model="selectedTag"
      :options="tagOptions"
      :multiple="true"
    ></multiselect> -->

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

    <ul>
      <li v-for="item in filteredProducts" :key="item.id">
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  components: {},

  data() {
    return {
      selectedTags: [],
    };
  },
  methods: {
    updateSelectedTags() {
      this.$emit("update:selected-tags", this.selectedTags);
    },
  },
};
</script>
