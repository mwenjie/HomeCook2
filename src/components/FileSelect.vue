<template>
  <label class="file-select cursor-pointer">
    <link
      href="https://fonts.googleapis.com/icon?family=Material+Icons"
      rel="stylesheet"
    />
    <div class="border rounded-lg w-48 h-48 py-1 px-1">
      <span>
        <i class="material-icons circle-icon">add</i>
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

  methods: {
    handleFileChange: function(event) {
      var input = event.target;
      // Ensure that you have a file before attempting to read it
      if (input.files && input.files[0]) {
      // create a new FileReader to read this image and convert to base64 format
        var reader = new FileReader();
        // Define a callback function to run, when FileReader finishes its job
        reader.onload = (e) => {
        // Note: arrow function used here, so that "this.imageData" refers to the imageData of Vue component
        // Read image as base64 and set to imageData
        this.$emit("selected", e.target.result);
        }
        // Start the reader job - read file as a data url (base64 format)
        reader.readAsDataURL(input.files[0]);
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
  padding: 5px;
  border-radius: 50%;
  border: 2px solid lightgrey;
  cursor: pointer;
}
</style>
