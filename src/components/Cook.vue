<template>
  <div class="flex bg-grey-lighter">
    <div class="flex-initial border-r-2">
      <ul class="list-reset w-48 ml-8">
        <li class="mt-10">Published recipes</li>
        <li class="mt-5">Cooks I follow</li>
      </ul>
    </div>
    <div>
      <ul class="list-reset inline-flex flex-wrap mt-2">
        <div class="flex-col mb-2" v-for="item in items">
          <img class="border rounded-lg w-48 h-48 ml-2" :src="item.imgBase64"/>
          <p class="text-center text-sm">{{ item.title }}</p>
        </div>
        <div class="ml-2 w-48 h-48"><file-select @selected="saveFiles"></file-select></div>
      </ul>
      <Modal :file1=this.files @close="closeModal" v-if="isModalVisible">
      </Modal>
    </div>
  </div>
</template>

<script>
import FileSelect from "./FileSelect";
import Modal from "./Modal";

export default {
  components: {
    FileSelect,
    Modal
  },
  data() {
    return {
      isModalVisible: false,
      files: [],
      items: [
      { imgBase64: "https://tailwindcss.com/img/card-top.jpg", title: "Mountain" }, 
      { imgBase64: "https://tailwindcss.com/img/card-left.jpg", title: "Coffee" }]
    }
  },
  methods: {
    saveFiles: function (files) {
      this.files = files;
      this.isModalVisible = true;
    }, 
    saveRecipe: function (recipe) {
      this.isModalVisible = false;
      console.log(recipe);
    },
    closeModal(){
      this.isModalVisible = false;
    }
  }
};
</script>

<style>
.btn {
  color: white;
  background: #000;
  border: 1px solid #828282;
  border-radius: 2px;
  margin: 4px;
  padding: 5px;
}
</style>
