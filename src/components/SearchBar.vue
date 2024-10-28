<!-- eslint-disable prettier/prettier -->
<template>
  <div class="container-fluid">
        <div class="row">
        <div class="col-12 d-flex justify-content-start align-items-start p-3"> 
        <form>
            <input v-model="inputText" type="text" id="inputField" placeholder="Type here" class="form-control">
            <button class="btn btn-primary" @click="search"> Search</button>
        </form>
      

        </div>

  </div>
  </div>


</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      inputText: "",
    };
  },

  methods: {
    search() {
      this.$emit("search", this.inputText);
    },
  },
};
</script>

<style></style>
