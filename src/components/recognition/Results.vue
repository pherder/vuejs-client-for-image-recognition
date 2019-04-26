<template>
  <div>
    <div class="box go-back" @click="goBack">
      <h1>
        <img src="../../assets/home-icon.png" class="home-icon"> Recognition results
      </h1>
    </div>
    <div class="box no-padding">
      <img class="img-thumbnail" v-if="imageUrl" :src="imageUrl">
    </div>
    <div v-if="recognitionResults" class="box">
      <div class="result" v-for="(val, key, index) in recognitionResults" :key="index">
        <div class="result-title">{{ key }}</div>
        <div class="progress">
          <div class="progress-label">{{ val }}</div>
          <div class="progress-bar" :style="'width:' + val * 100 + '%'"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: {
    recognitionResults: Object,
    imageUrl: String
  },
  data() {
    return {};
  },
  methods: {
    goBack() {
      this.$emit("homeClicked", true);
    }
  },
  created: function() {}
};
</script>

<style scoped>
.go-back {
  cursor: pointer;
}
.result {
  margin-bottom: 0.5rem;
}

.result:last-child {
  margin-bottom: 0;
}

.result-title {
  font-weight: bold;
  text-align: left;
  margin-bottom: 0.2rem;
  text-transform: capitalize;
}

.progress {
  height: 1.5rem;
  background-color: #49666d;
  text-align: center;
  display: flex;
  align-items: center;
}

.progress-label {
  position: absolute;
  color: #eeffff;
  left: 50%;
  transform: translateX(-50%);
}

.progress-bar {
  height: 100%;
  background: #1f2833;
}
.home-icon {
  height: 1.5rem;
}
</style>
