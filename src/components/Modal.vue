<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="flex-col bg-white max-w-sm w-full">
        <div class="flex justify-between bg-grey-lighter py-1 px-1 border-b">
          <div class="font-sans text-sm font-medium py-1 px-1">Create Recipe</div>
          <i class="material-icons cursor-pointer" @click="close">close</i>
        </div>
        <div class="flex justify-start py-1 px-1 border-b pl-1">
          <i class="material-icons">account_circle</i>
          <input
            class="font-sans text-sm font-medium px-1 py-1 focus:outline-none"
            type="text"
            placeholder="Give your recipe a title"
          />
        </div>
        <div class="flex justify-start mt-1 my-1 mx-1 border-b flex-no-wrap overflow-x-scroll">
          <div v-for="(item, index) in imageData">
            <div class="relative">
              <div class="border rounded-lg h-24 w-24 ml-1 mb-1 cursor-pointer"
              :style="{ backgroundImage: 'url(' + item + ')'  }" 
             style="background-size:cover"
             v-bind:class="{ 'border-orange border-t-2 border-r-2 border-l-2 border-b-2': index == selectedImage }"
              @click="selectedImage = index" 
             />
             <i class="fa fa-star absolute pin-t pin-r bg-grey-lighter cursor-pointer" title="Album Cover"
              v-show="index == selectedImage"
            />
            </div>
          </div>
          <div class="relative">
            <div class="mx-1 w-24 h-24 mb-1"><file-select @selected="showModal"></file-select></div>
         </div>
        </div>
        <div class="flex-col mx-1 my-1">
          <div class="font-sans text-sm font-medium px-1">Introduction</div>
          <div class="font-sans text-xs font-small text-grey px-1 mb-1">Tell us about it. What secret ingredients did you add?</div>
          <textarea class="border w-full h-24"></textarea>
        </div>
        <div class="flex-col mx-1 my-1">
          <div class="font-sans text-sm font-medium px-2">Ingredients</div>
          <div class="font-sans text-xs font-small text-grey px-2 mb-1">Didn't measure exactly? No worries. Approximate and mention it in the cook's note, below.</div>
          <draggable v-model="exampleList">
             <div v-for="(item, index) in exampleList">
              <div class="flex w-full justify-start items-center mb-2 border-b h-8"
               @mouseover="selectedItem = index" @mouseleave="selectedItem = -1">
                <div class="text-xs font-extrabold cursor-pointer" v-show="index == selectedItem" @click="vdelete(index)">X</div>
                <div class="text-xs font-extrabold text-transparent" v-show="index != selectedItem">X</div>
                <input class="appearance-none bg-transparent border-none w-48 focus:outline-none" type="text">
                <i class="pl-32 fa fa-bars fa-xs cursor-move" v-show="index == selectedItem"></i>
              </div>
             </div>
          </draggable>
         <div class="text-xs font-extrabold cursor-pointer">+ Add Ingredients</div>
       </div>
      </div>
    </div>
  </transition>
</template>

<script>
import FileSelect from "./FileSelect";
import draggable from 'vuedraggable';

export default {
  components: {
    FileSelect,
    draggable
  },
  props: ["file1"],
  name: "Modal",
  data: () => ({
    isActive: true,
    selectedImage: 0,
    selectedItem: 0,
    imageData: [
     "https://tailwindcss.com/img/card-top.jpg",
     "https://tailwindcss.com/img/card-left.jpg",
     "https://i.ibb.co/GHcX72k/110060-00-2x.png",
     "https://i.ibb.co/0q5Q4hV/Untitled.png",
     "https://i.ibb.co/0q5Q4hV/Untitled.png"
    ],
    exampleList: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4',
        'Item 5'
    ]
  }),
  methods: {
    close() {
      this.$emit("close");
    },
    showModal: function (files) {
      this.isModalVisible = true;
      this.files = files;
    },
    vdelete(index) {
      this.exampleList.splice(index,1);
    }
  }
};
</script>

<style>
.modal-fade-enter,
.modal-fade-leave-active {
  opacity: 0;
}
.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.5s ease;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
