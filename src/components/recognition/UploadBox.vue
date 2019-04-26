<template>
  <div class="box">
    <h1>Recognise your image!</h1>
    <div class="drop-box" :class="hover">
      <p v-html="message"></p>
      <input
        type="file"
        @dragover="onDragOver"
        @dragleave="onDragLeaveOrDrop"
        @drop="onDragLeaveOrDrop"
        class="input-file"
        @change="onFileSelected"
        accept="image/x-png, image/jpeg"
      >
    </div>
    <img class="img-thumbnail" v-if="imageUrl" :src="imageUrl">
    <button class="btn" @click="onUpload">ANALYZE</button>
  </div>
</template> 

<script>
export default {
  name: "UploadBox",
  data() {
    return {
      message: null,
      text: "drag&drop your image here or click to browse",
      file: null,
      imageUrl: null,
      hover: null
    };
  },
  methods: {
    onFileSelected(event) {
      this.file = event.target.files[0];
      this.imageUrl = URL.createObjectURL(this.file);
      this.hover = "";
      this.text = "you've selected: <br>" + this.file.name;
      this.message = this.text;
    },
    onDragOver() {
      this.message = "drop file now";
      this.hover = "hover";
    },
    onDragLeaveOrDrop() {
      this.hover = "";
      this.message = this.text;
    },
    onUpload() {
      this.$emit("uploadClicked", this.file);
    }
  },
  created: function() {
    this.message = this.text;
  }
};
</script>

<style scoped>
h1 {
  margin-bottom: 1.5rem;
}

.drop-box {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  border: 1px dashed #004444;
  height: 6rem;
  transition: all 0.3s;
  border-radius: 0.5rem;
  margin-bottom: 1.5rem;
}

.drop-box:hover,
.drop-box.hover {
  background: #004444;
  color: #eeffff;
}

.input-file {
  cursor: pointer;
  position: absolute;
  left: 0;
  top: 0;
  opacity: 0;
  width: 100%;
  height: 100%;
}

.img-thumbnail {
  margin-bottom: 1.5rem;
}
</style>
