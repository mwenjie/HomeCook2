<template>
  <label class="file-select cursor-pointer">
    <link
      href="https://fonts.googleapis.com/icon?family=Material+Icons"
      rel="stylesheet"
    />
    <div class="border border-dashed rounded-lg w-full h-full py-1 px-1">
      <span>
        <i class="material-icons circle-icon" style="font-size: 18px">add</i>
      </span>
    </div>
    <input type="file" @change="handleFileChange" multiple/>
  </label>
</template>

<script>
export default {
  props: {
    value: ''
  },
  data() {
    return {
      imgStore: []
    }
  },
  methods: {
    handleFileChange: function(event) {
      var input = event.target;
      var files =  [];
      if (input.files && input.files[0]) {
        var files_count = input.files.length;
        for (let i=0; i<files_count; i++){
          var reader = new FileReader();
          reader.onload = (e) => {
            this.$emit("selected1", e.target.result);
            files.push(e.target.result);
          }
          reader.readAsDataURL(input.files[i]);
        }
        this.$emit("selected", files);
      }
    }
  }
};
</script>

<style scoped>

.file-select > input[type="file"] {
  display: none;
}

.circle-icon {
  border-radius: 50%;
  border: 2px solid lightgrey;
  cursor: pointer;
}
</style>
