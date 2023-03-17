<template>
  <div class="hello grid-container">
    <div
      v-for="i in 4"
      :key="i"
      :style="{ top: '0px', left: (i-1)*20+'%' }"
      class="image-container"
    >
      <img :src="require(`@/assets/img/egg.png`)" class="image" />
    </div>
      <div
      v-for="i in 5"
      :key="i"
      :style="{ bottom: '0px', left: (i-1)*20+'%' }"
      class="image-container"
    >
      <img :src="require(`@/assets/img/heart.png`)" class="image" />
    </div>
    <el-image
        class="bg"
        :src="require(`@/assets/img/p${currentIndex+1}.jpg`)"
        fit="fill"></el-image>
    <header>
        <div class="mirror">
          <video ref="video" autoplay></video>
        </div>
    </header>
    <main>
      <div class="carl">
        <el-carousel  ref="carl" @change="carouselChange" :interval="7000000" card-width="700" type="card" height="500px">
          <el-carousel-item>
            <SlideOne/>
          </el-carousel-item>
          <el-carousel-item>
            <SlideTwo/>
          </el-carousel-item>
          <el-carousel-item>
            <SlideThree/>
          </el-carousel-item>
          <el-carousel-item>
            <SlideFour/>
          </el-carousel-item>
        </el-carousel>
      </div>
    </main>

    <footer>Designed by Bryan • <a href="https://github.com/alexwidua/prototypes" target="_blank" rel="noopener">Github</a></footer>
        
  </div>
</template>

<script>
import SlideOne from './slides/SlideOne.vue'
import SlideTwo from './slides/SlideOne.vue'
import SlideThree from './slides/SlideOne.vue'
import SlideFour from './slides/SlideOne.vue'
export default {
  name: 'HelloWorld',
  data() {
    return {
      currentIndex: 0,
      numIcons:8,
      radius:150
    }
  },
  components: {
    SlideOne,
    SlideTwo,
    SlideThree,
    SlideFour,
  },
  props: {
    msg: String
  },
  created() {
    navigator.mediaDevices.getUserMedia({ video: { facingMode: "user" } })
      .then(stream => {
        this.$refs.video.srcObject = stream;
      })
      .catch(error => {
        console.log(error);
      });
  },
  mounted() {
    const carl = this.$refs.carl.$el
    carl.addEventListener("wheel",this.handleWheel)
  },
  beforeUnmount() {
    const carl = this.$refs.carl.$el
    carl.removeEventListener("wheel",this.handleWheel)
  },
  methods:{
    carouselChange(index){
      this.currentIndex = index
    },
    handleWheel(e){
      const delta = e.deltaY
      const carl = this.$refs.carl
      if(delta>0){
        carl.next()
      }else{
        carl.prev()
      }
    }
  }

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.image-container {
  position: absolute;
  width: 13%;
  height: 13%;
  transform: translate(-50%, -50%);
  display: flex;
  justify-content: center;
  align-items: center;

  z-index: 3;
  margin: 45px 35px -35px 90px;
}
.image {
  max-width: 100%;
  max-height: 100%;
}

.hello{height: 100%;}
.grid-container{
    display: grid;
    grid-template-rows: 100px 1fr 50px;
    grid-template-areas:
    'header'
    'main'
    'footer';
}


.mirror { 
  height: 100%;
  width: 80px;
  float: right;
  border-radius: 50%;
  overflow: hidden;  

  margin-right: 80px
}
.mirror::after{
  content: '';
  position: absolute;
  height: 80px;
  width: 80px;
  background-image: url('../assets/img/demon.png');
  background-size: cover;
  background-position: center;
  right: 80px;
}
.carl {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

video {
  height: 100%;
  width: 100%;
  object-fit: cover;

  transform: scaleX(-1);
}


.el-carousel__item {
    width: 70%;
    left: -10%;
}

.el-carousel__item:nth-child(3) {
    background-image: url('../assets/img/p1.jpg');
    background-size: cover;
    background-position: center;
}

.el-carousel__item:nth-child(4) {
    background-image: url('../assets/img/p2.jpg');
    background-size: cover;
    background-position: center;
}

.el-carousel__item:nth-child(5) {
    background-image: url('../assets/img/p3.jpg');
    background-size: cover;
    background-position: center;
}

.el-carousel__item:nth-child(6) {
    background-image: url('../assets/img/p4.jpg');
    background-size: cover;
    background-position: center;
}

header{
  grid-area: header;
  z-index: 1;

  padding: 10px;
}
main{
  grid-area: main;
}
footer{
  grid-area: footer;
  z-index: 1;
}

.bg{
    position: absolute;
    top: 0;
    object-fit: fill;
    left: 0;
    width: 100%;
    height: 100%;

    filter: blur(40px);
}
.bg::after{
  content: "";
  display: block;
  background: rgba(0,0,0,0.5);
  z-index:1;
}
</style>
