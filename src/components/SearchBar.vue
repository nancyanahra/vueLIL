<!-- eslint-disable prettier/prettier -->
<template>
  <div class="container-fluid">
        <div class="row">
        <div class="col-12 d-flex justify-content-start align-items-start p-3"> 
        <form>
            <input v-model="inputText" type="text" id="inputField" @input="search" placeholder="Search for items here" class="form-control">
    
        </form>
      
        </div>

  </div>
  </div>


</template>

<script>
import { toRefs, ref, watch } from "vue";

export default {
  name: "SearchBar",
  emits: ["search"],
  setup(props, { emit }) {
    const inputText = ref("");

    const search = () => {
      emit("search", inputText.value);
    };
    return {
      inputText,
      search,
    };
  },
};
</script>

<style></style>
