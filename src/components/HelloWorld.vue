<template>
  <div class="hello grid-container">
    <meting-js
      server="netease"
      type="playlist"
      id="7263067958"
      fixed="true"
      autoplay="true"
      loop="all"
      order="list"
      preload="auto"
      list-folded="true"
      list-max-height="500px"
      lrc-type="1"
    >
    </meting-js>
    <div class="letter" ref="letter">
      <button @click="handleBackClick">
        <el-icon><CloseBold /></el-icon>
      </button>
      <div class="paper">
        <div class='fla'></div>
        <h1 class="title">{{ title }}</h1>
        <p class="l-content">to: 小狗</p>
        <p class="l-content">{{ content }}</p>
        <p class="l-content">{{ content2 }}</p>
        <p class="l-content">{{ content3 }}</p>
        <p class="l-content">{{ content4 }}</p>
        <p class="l-content">{{ content5 }}</p>
        <p class="l-content">{{ content6 }}</p>
        <p class="l-content">{{ content7 }}</p>
        <p class="l-content">{{ content8 }}</p>
         <p class="l-content">{{ content9 }}</p>
      </div>
    </div>
    <div class="envelope-container" ref="envelope">
      <div class="envelope"></div>
      <div class="card" id="test" @click="handleCardClick">
        <h1 class="message">WILL YOU BE MY VALENTINE?</h1>
      </div>
      <div class="cover"></div>
      <div class="lid"></div>
    </div>
    <div
      v-for="i in 4"
      :key="i"
      :style="{ top: '0px', left: (i - 1) * 20 + '%' }"
      class="image-container"
    >
      <img :src="require(`@/assets/img/egg.png`)" class="image" />
    </div>
    <div
      v-for="i in 7"
      :key="i"
      :style="{ bottom: '35px', left: (i - 1) * (100 / 7) + '%' }"
      class="image-container"
    >
      <img
        :src="require(`@/assets/img/heart.png`)"
        class="image heart content"
        @click="handleHeartClick"
      />
    </div>
    <el-image
      class="bg"
      :src="require(`@/assets/img/p${currentIndex + 1}.jpg`)"
      fit="fill"
    ></el-image>
    <header>
      <div class="mirror">
        <video ref="video" autoplay></video>
      </div>
    </header>
    <main>
      <div class="carl">
        <el-carousel
          ref="carl"
          @change="carouselChange"
          :interval="7000000"
          card-width="700"
          type="card"
          height="500px"
        >
          <el-carousel-item>
            <i class="love fa fa-heart" @click="markHeart($event, 1)"></i>
            <SlideOne />
          </el-carousel-item>
          <el-carousel-item>
            <i class="love fa fa-heart" @click="markHeart($event, 2)"></i>
            <SlideTwo />
          </el-carousel-item>
          <el-carousel-item>
            <i class="love fa fa-heart" @click="markHeart($event, 3)"></i>
            <SlideThree />
          </el-carousel-item>
          <el-carousel-item>
            <i class="love fa fa-heart" @click="markHeart($event, 4)"></i>
            <SlideFour />
          </el-carousel-item>
          <el-carousel-item>
            <i class="love fa fa-heart" @click="markHeart($event, 5)"></i>
            <SlideFive />
          </el-carousel-item>
          <el-carousel-item>
            <i class="love fa fa-heart" @click="markHeart($event, 6)"></i>
            <SlideSix />
          </el-carousel-item>
          <el-carousel-item>
            <i class="love fa fa-heart" @click="markHeart($event, 7)"></i>
            <SlideSeven />
          </el-carousel-item>
        </el-carousel>
      </div>
    </main>

    <footer>
      Designed by Bryan •
      <a
        href="https://github.com/jinhualong-elixir/jinhualong-elixir.github.io"
        target="_blank"
        rel="noopener"
        >Github</a
      >
    </footer>
  </div>
</template>

<script>
import SlideOne from "./slides/SlideOne.vue";
import SlideTwo from "./slides/SlideTwo.vue";
import SlideThree from "./slides/SlideThree.vue";
import SlideFour from "./slides/SlideFour.vue";
import SlideFive from "./slides/SlideFive.vue";
import SlideSix from "./slides/SlideSix.vue";
import SlideSeven from "./slides/SlideSeven.vue";
export default {
  name: "HelloWorld",
  data() {
    return {
      currentIndex: 0,
      numIcons: 8,
      radius: 150,
      title: "一封情书",
      content:
        '"南伊豆是小阳春天气，一尘不染，晶莹透明，实在美极了。在浴池下方的上涨的小河，承受着暖融融的阳光，。昨夜的烦躁，自己也觉得如梦似幻"',
      content2:
        '我不知道伊豆的风景，但在他的眼里一定是如那个女孩一样明媚。而我也许是因为某位小狗的缘故，也爱上了杭州城的风景，我的情愫在那个亭子里徘徊，我的悸动从苏堤的这头折腾到了那头。'
      ,content3:
        '好喜欢你'
        ,content4:
        '说到心的悸动，还记得那个昏暗的威士忌吧么，有那一刻你眼睛的存在是那么显眼，让忘记了自己正聊着的话题，我只是看着你。'
        ,content5:
        '这就是我对你感情的开端了，在之后我们的进展顺利地让我有种梦幻的感觉，从并排散步到牵手...你有时候会和我抱怨是不是太快了，不过宝贝，我们才不是那种来去匆匆的浮躁都市男女呢'
        ,content6:
        '而你就像KFC一样，第一次尝试就爱上了，每周都吃不腻'
        ,content7:
        '好喜欢你'
        ,content8:
        '现在的我正在磕磕绊绊地组织着语言，心里对你的爱意却越来越浓厚。这个周末我继续搂着你闲聊吧，而小狗请不要忘记到我的怀里蹭蹭，我真的真的很需要这个'
        ,content9:
        '爱你的: "小娇妻"'
   };
  },
  components: {
    SlideOne,
    SlideTwo,
    SlideThree,
    SlideFour,
    SlideFive,
    SlideSix,
    SlideSeven,
  },
  props: {
    msg: String,
  },
  created() {
    navigator.mediaDevices
      .getUserMedia({ video: { facingMode: "user" } })
      .then((stream) => {
        this.$refs.video.srcObject = stream;
      })
      .catch((error) => {
        console.log(error);
      });
  },
  mounted() {
    const carl = this.$refs.carl.$el;
    carl.addEventListener("wheel", this.handleWheel);
  },
  beforeUnmount() {
    const carl = this.$refs.carl.$el;
    carl.removeEventListener("wheel", this.handleWheel);
  },
  methods: {
    handleHeartClick(e) {
      if (e.target.classList.contains("special")) {
        this.$refs.envelope.classList.toggle("actived");
      }
    },
    handleBackClick() {
      this.$refs.letter.classList.toggle("expanded");
      this.$refs.envelope.classList.toggle("actived");
    },
    handleCardClick() {
      this.$refs.letter.classList.toggle("expanded");
    },
    carouselChange(index) {
      this.currentIndex = index;
    },
    handleWheel(e) {
      const delta = e.deltaY;
      const carl = this.$refs.carl;
      if (delta > 0) {
        carl.next();
      } else {
        carl.prev();
      }
    },
    markHeart(e, i) {
      e.target.classList.toggle("active");

      let heartList = document.getElementsByClassName("heart");
      if (e.target.classList.contains("active")) {
        heartList[i - 1].classList.add("actived");
      } else {
        heartList[i - 1].classList.remove("actived");
      }

      if (document.getElementsByClassName("actived").length == 7) {
        heartList[heartList.length - 1].classList.add("special");
      } else {
        heartList[heartList.length - 1].classList.remove("special");
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.fla{
 margin: 50px;
  float: right;
  width: 140px;
  height: 206px;
  background-image: url("../assets/img/flamingo.png");
  background-size: cover;
}
h1,
p {
  font-family: yinhexi, Arial, Helvetica, sans-serif;
}
.el-icon {
  font-size: 40px;
}
@keyframes open {
  100% {
    transform: rotatex(180deg);
  }
}
/*信件合上的动画*/
@keyframes open-rev {
  from {
    transform: rotatex(-180deg);
  }
}
.card {
  position: absolute;
  /*白色的卡片*/
  background: white;
  height: 25vmin;
  width: 43vmin;
  display: flex;
  /*设置div水平显示*/
  flex-direction: column;
  /*设置flex子项在每个flex行的交叉轴上的中心对齐，交叉轴方向为column，即垂直方向**/
  align-items: center;
  /*设置flex子项在主轴上的中心对齐*/
  justify-content: center;
  left: 2.5vmin;
  top: 0vmin;
  cursor: pointer;
  animation: slide-rev 0.2s ease-out;

  -webkit-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  -moz-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
  -o-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
}
.letter {
  position: absolute;
  top: 0;
  left: 0;
  margin: 53px;
  height: 80%;
  width: 90%;
  opacity: 0;
  background: white;
  transition: all 0.8s ease-in-out;
  button {
    position: absolute;
    top: 20px;
    left: 20px;
    z-index: 1;
  }
  h1,
  p {
    color: black;
    display: none;
  }
}

.letter.expanded {
  z-index: 999;
  opacity: 1;
  -webkit-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  -moz-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
  -o-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;

  h1,
  p {
    display: block;
  }
}

.paper {
  width: 100%;
  height: 100%;
  background-color: #fff;
  border: 1px solid #ccc;
  overflow-y: scroll;
  :nth-child(3){
    text-align: left;
  }
  :last-child{
    text-align: right;
  }
}
.title {
  font-size: 40px;
  font-weight: bold;
  margin-bottom: 20px;
  padding: 50px 0px 50px 150px;
}

.l-content {
  font-size: 20px;
  line-height: 1.5;
  text-align: center;
  padding: 50px 150px 50px 150px;
}
.paper:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: url("https://dogefs.s3.ladydaily.com/~/source/unsplash/photo-1586074299757-dc655f18518c?ixlib=rb-4.0.3&q=85&fmt=jpg&crop=entropy&cs=srgb&dl=marjan-blan-marjanblan-794QUz5-cso-unsplash.jpg");
  opacity: 0.3;
}

/*卡片从右侧滑入*/
@keyframes slideL {
  100% {
    transform: translatex(-100vmin);
  }
}
@keyframes slideL-rev {
  from {
    transform: translatex(-100vmin);
  }
}
.envelope-container.actived {
  /*卡片划出动画*/
  animation: slideL .8s;
  animation-delay: 0.3s;
  /*把卡面动画地从一个地方移动到另一个地方，并让它停留在那里。*/
  animation-fill-mode: forwards;
}
.envelope-container:not(.actived) {
  /*卡片划出动画*/
  animation: slideL-rev 1.0s;
  animation-fill-mode: forwards;
}
.envelope-container:hover .card {
  /*卡片划出动画*/
  animation: slide 0.2s;
  animation-delay: 0.5s;
  /*把卡面动画地从一个地方移动到另一个地方，并让它停留在那里。*/
  animation-fill-mode: forwards;
}

/*卡片划出信封*/
@keyframes slide {
  100% {
    transform: translatey(-15vmin);
    z-index: 2;
  }
}
/*卡片落回信封*/
@keyframes slide-rev {
  from {
    transform: translatey(-15vmin);
  }
}
.lid {
  position: absolute;
  height: 0;
  width: 0;

  border-top: 15vmin solid #ff8896;
  border-left: 24vmin solid transparent;
  border-right: 24vmin solid transparent;

  top: 0;
  /*设置旋转元素的基点位置，为盒子的顶部边缘*/
  transform-origin: top;
  animation: open-rev 2s;
}

.envelope-container:hover .lid {
  animation: open 0.5s;
  animation-fill-mode: forwards;
}
.cover {
  position: absolute;
  height: 0;
  width: 0;

  border-bottom: 15vmin solid #f5b5bb;
  border-left: 24vmin solid transparent;
  border-right: 24vmin solid transparent;
  top: 15vmin;
  z-index: 3;
}

.cover::after {
  /*left triangle*/
  position: absolute;
  content: "";
  border-left: 24.5vmin solid #ffbbc1;
  border-bottom: 15vmin solid transparent;
  border-top: 15vmin solid transparent;
  top: -15vmin;
  left: -24vmin;
}

.cover::before {
  position: absolute;
  content: "";
  border-right: 24.5vmin solid #ffbbc1;
  border-bottom: 15vmin solid transparent;
  border-top: 15vmin solid transparent;
  top: -15vmin;
  left: -0.5vmin;
}
.envelope-container {
  position: absolute;
  top: 50%;
  left: 120%;
  margin: -15vmin 0 0 -24vmin;
  z-index: 998;

  -webkit-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  -moz-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
  -o-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
}
.envelope-container::after{
  content: "";
  z-index: 998;
  position: absolute;
  right: -247px;
  top: -66px;
  display: block;
  width: 80%;
  height: 200%;
  background-image: url("../assets/img/myHandT.png");
  background-size: cover;
  transform: rotate(270deg) scaleX(1);
} 
/*相对定位，并设置背景色和大小*/
.envelope {
  position: relative;
  background: #eb7885;
  height: 30vmin;
  width: 48vmin;
}
.love {
  font-size: 2.5rem;
  position: absolute;
  top: 30px;
  right: 30px;
}
// .love:hover{
//   color: red;
// }
.love.active {
  color: red;
}
.heart {
  filter: grayscale(1);
}
.heart.actived {
  filter: unset;
}

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

.hello {
  height: 100%;
}
.grid-container {
  display: grid;
  grid-template-rows: 100px 1fr 30px;
  grid-template-areas:
    "header"
    "main"
    "footer";
}

.mirror {
  height: 100%;
  width: 80px;
  float: right;
  border-radius: 50%;
  overflow: hidden;

  margin-right: 80px;

  -webkit-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  -moz-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
  -o-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
}
.mirror::after {
  content: "";
  position: absolute;
  height: 80px;
  width: 80px;
  background-image: url("../assets/img/demon.png");
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
  display: flex;
  flex-direction: column;
  justify-content: center;

  -webkit-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  -moz-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3),
    0 0 40px rgba(0, 0, 0, 0.1) inset;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
  -o-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
}

.el-carousel__item:hover {
  .page::after {
    opacity: 0.55;
    z-index: -1;
  }
  .page {
    opacity: 1;
    background: transparent;
  }
}

.el-carousel__item:nth-child(3) {
  background-image: url("../assets/img/p1.jpg");
  background-size: cover;
  background-position: center;
}

.el-carousel__item:nth-child(4) {
  background-image: url("../assets/img/p2.jpg");
  background-size: cover;
  background-position: center;
}

.el-carousel__item:nth-child(5) {
  background-image: url("../assets/img/p3.jpg");
  background-size: cover;
  background-position: center;
}

.el-carousel__item:nth-child(6) {
  background-image: url("../assets/img/p4.jpg");
  background-size: cover;
  background-position: center;
}

.el-carousel__item:nth-child(7) {
  background-image: url("../assets/img/p5.jpg");
  background-size: cover;
  background-position: center;
}

.el-carousel__item:nth-child(8) {
  background-image: url("../assets/img/p6.jpg");
  background-size: cover;
  background-position: center;
}

.el-carousel__item:nth-child(9) {
  background-image: url("../assets/img/p7.jpg");
  background-size: cover;
  background-position: center;
}

header {
  grid-area: header;
  z-index: 1;

  padding: 10px;
}
main {
  grid-area: main;
}
footer {
  grid-area: footer;
  background: black;
  z-index: 1;
  text-align: end;
  line-height: 30px;
  a {
    color:#a2a1a1;
    margin-right: 20px;
  }
}

.bg {
  position: absolute;
  top: 0;
  object-fit: fill;
  left: 0;
  width: 100%;
  height: 100%;

  filter: blur(40px);
}
.bg::after {
  content: "";
  display: block;
  background: rgba(0, 0, 0, 0.5);
  z-index: 1;
}

@keyframes zy {
  10% {
    transform: rotate(15deg);
  }
  20% {
    transform: rotate(-10deg);
  }
  30% {
    transform: rotate(5deg);
  }
  40% {
    transform: rotate(-5deg);
  }
  50%,
  100% {
    transform: rotate(0deg);
  }
}
/* 使用 */
.content.actived {
  animation: zy 2.5s 0.15s linear infinite;
  animation: zy 2.5s 0.15s linear infinite;
  animation: zy 2.5s 0.15s linear infinite;
  animation: zy 2.5s 0.15s linear infinite;
}

.content:hover {
  animation: unset;
  transform: scale(1.05);
}

.special {
  animation: zy 0.5s 0.05s linear infinite !important;
  animation: zy 0.5s 0.05s linear infinite !important;
  animation: zy 0.5s 0.05s linear infinite !important;
  animation: zy 0.5s 0.05s linear infinite !important;
}
.special:hover {
  animation: unset !important;
  transform: scale(1.05);
}
.special:active {
  transform: scale(1);
}

// /* 兼容写法 */
// animation: zy 2.5s .15s linear infinite;
// -moz-animation: zy 2.5s .15s linear infinite; /* Firefox */
// -webkit-animation: zy 2.5s .15s linear infinite; /* Safari and Chrome */
// -o-animation: zy 2.5s .15s linear infinite; /* Opera */

.card h1 {
  color: #000000;
}

.card:hover {
}
</style>
