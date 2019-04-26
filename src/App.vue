<template>
  <div id="app">
    <!--
    <div id="nav">
      <router-link to="/">Car recognition</router-link>
    </div>
    -->
    <router-view/>
  </div>
</template>

<script>
  export default {};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: "Montserrat", Helvetica, Arial, sans-serif;
}

#app {
  text-align: center;
  color: #2c3e50;
}

.box {
  background: linear-gradient(#0ff, #0cc);
  width: 33rem;
  padding: 2rem;
  margin-bottom: 1rem;
  border-radius: 0.2rem;
}

@media (max-width: 550px) {
  .box {
    width: auto;
    margin-left: 1rem;
    margin-right: 1rem;
  }
}

.img-thumbnail {
  width: 100%;
  vertical-align: middle;
  max-height: 25rem;
  object-fit: contain;
}

.btn {
  cursor: pointer;
  background: none;
  border: 1px solid #004444;
  border-radius: 0.5rem;
  padding: 1rem;
  transition: all 0.3s;
  width: 100%;
  font-size: 1rem;
  font-weight: bold;
  color: #004444;
}

.btn:hover {
  background: #004444;
  color: #eeffff;
}

.no-padding {
  padding: 0;
}
</style>
