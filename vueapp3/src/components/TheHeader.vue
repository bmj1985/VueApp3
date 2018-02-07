<template>
  <header>
    <img :src="img" alt="">
  </header>
</template>

<script>
export default {
  name: 'TheHeader',
  data() {
    return {
      img: '../../static/g-dino.png'
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
  grid-row: 1/3;
  grid-column: 1/2;
  height: 100px;
  width: auto;
}
</style>
