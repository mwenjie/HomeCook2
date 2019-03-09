<script>
export default {
  props: ['file1'],
  name: "Modal",
  data: () => ({
    author: "",
    name: ""
  }),
  methods: {
    close() {
      this.$emit("close");
    }
  }
};
</script>

<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="flex-col bg-white max-w-sm w-full">
        <div class="flex justify-between bg-grey-lighter py-1 px-1 border-b ">
          <div class="font-sans text-sm font-medium py-1">Create Recipe</div>
          <i class="material-icons cursor-pointer" @click="close">close</i>
        </div>
       <div class="flex justify-start py-1 px-1 border-b pl-1">
          <i class="material-icons">account_circle</i>
          <input class="font-sans text-sm font-medium px-1 py-1 focus:outline-none" type="text" placeholder="Say Something">
       </div>
       <div class="flex justify-start mt-2 py-1 px-1 border-b pl-1">
          <img class="border rounded-lg w-24 h-24 ml-2" :src="this.file1">
       </div>
      </div>
    </div>
  </transition>
</template>

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

.modal-header,
.modal-footer {
  padding: 5px;
  text-align: center;
}
.modal-footer {
  border-top: 1px solid #eeeeee;
  justify-content: flex-end;
}
.btn-close {
  border: none;
  font-size: 20px;
  padding: 20px;
  cursor: pointer;
  font-weight: bold;
  color: #000;
  background: transparent;
  text-align: right;
}
.btn-green {
  color: white;
  background: #828282;
  border: 1px solid #828282;
  border-radius: 2px;
  margin: 5px;
}
.input {
  margin-top: 5px;
}
.added-text {
  margin-block-end: -10px;
  margin-block-start: 0.5rem;
}
</style>
