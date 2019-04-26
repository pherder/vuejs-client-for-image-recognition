<template>
  <div class="recognition">
    <BackgroundImage/>
    <transition name="fade" mode="out-in">
      <UploadBox @uploadClicked="exampleUploadImage" v-if="state === 0"/>
      <Processing v-if="state === 1"/>
      <Results
        @homeClicked="showHome"
        :imageUrl="imageUrl"
        :recognitionResults="recognitionResults"
        v-if="state === 2"
      />
    </transition>
  </div>
</template>

<script>
import axios from "axios";
import BackgroundImage from "@/components/recognition/BackgroundImage.vue";
import UploadBox from "@/components/recognition/UploadBox.vue";
import Processing from "@/components/recognition/Processing.vue";
import Results from "@/components/recognition/Results.vue";

export default {
  name: "Recognition",
  components: {
    BackgroundImage,
    UploadBox,
    Processing,
    Results
  },
  data() {
    return {
      state: 0,
      apiUri: "http://127.0.0.1:5000/upload/",
      imageUrl: null,
      recognitionResults: null
    };
  },
  methods: {
    uploadImage(image) {
      try {
        this.imageUrl = URL.createObjectURL(image);
      } catch (error) {
        alert("First select a file!");
        return;
      }
      this.state = 1;
      var formData = new FormData();
      formData.append("file", image, image.name);
      axios
        .post(this.apiUri, formData)
        .then(response => {
          this.recognitionResults = response.data;
          this.state = 2;
        })
        .catch(error => {
          console.log(error.message);
          alert("No connection with the server.");
          this.state = 0;
        });
    },
    exampleUploadImage(image) {
      try {
        this.imageUrl = URL.createObjectURL(image);
      } catch (error) {
        alert("First select a file!");
        return;
      }
      this.state = 1;
      this.recognitionResults = {
        "Here are some": "1.00",
        "example results": "0.75",
        "from object": "0.50",
        "recognitionResults": "0.00"
      };
      var that = this;
      setTimeout(function() {
        that.state = 2;
      }, 1500);
    },
    showHome() {
      this.state = 0;
    }
  }
};
</script>

<style scoped>
.recognition {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100vh;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
