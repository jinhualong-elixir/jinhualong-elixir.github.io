<template>
  <div class="page">
      <h2>test test test</h2>
      <p>test test testtest test test</p>
  </div>
</template>

<script>
export default {
  name: 'SlideOne',
  data() {
    return {
      url: 'https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg'
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,h2,h3,h4,h5,h6{
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
}
p{
  font-family: Verdana, sans-serif;
  font-size: 16px;
  line-height: 1.5;
  color: #333333;
}

.page{
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}


</style>
