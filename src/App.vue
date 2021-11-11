<template>
  <div id="wrapper">
    <div
      class="container"
      :style="`transform: translate(-50%, 50%) perspective(300px) rotateX(${x}deg) rotateY(${y}deg)`"
    >
      <div class="main">
        <div class="box1a">BOX</div>
        <div class="box1b"></div>
        <div class="box1c"></div>
        <div class="box1d"></div>
      </div>
      <div class="sec">
        <div class="box2A"></div>
        <div class="box2B"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      x: 0,
      y: 0,
    };
  },
  mounted() {
    document.addEventListener("mousemove", this.getCursorPosition);
    // window.addEventListener("resize", this.updateViewportSize);
  },
  methods: {
    getCursorPosition(event) {
      console.log((event.pageX / window.innerWidth).toFixed(2));
      console.log((event.pageY / window.innerHeight).toFixed(2));
      this.y =
        ((event.pageX - window.innerWidth / 2) / window.innerWidth).toFixed(2) *
        34;
      this.x =
        ((event.pageY - window.innerHeight / 2) / window.innerHeight).toFixed(
          2
        ) * -34;
    },
  },
  computed: {
    styles() {
      return {
        y:
          ((event.pageX - window.innerWidth / 2) / window.innerWidth).toFixed(
            2
          ) * 34,
        x:
          ((event.pageY - window.innerHeight / 2) / window.innerHeight).toFixed(
            2
          ) * -34,
      };
    },
  },
};
</script>

<style>
html,
body,
#app {
  margin: 0;
  padding: 0;
}
#wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  position: relative;
  width: 100vw;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) perspective(200px) rotateX(-5deg)
    rotateY(-5deg);
  display: grid;
  grid-template-columns: 60% 1fr;
  grid-template-rows: 240px;
  gap: 0px 0px;
  grid-template-areas: "main sec";
}
.main {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 0.7fr 1.3fr;
  gap: 0px 0px;
  grid-template-areas:
    "box1a box1b"
    "box1c box1d";
  grid-area: main;
}
.box1a {
  grid-area: box1a;
  font-size: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
}
.box1b {
  grid-area: box1b;
}
.box1c {
  grid-area: box1c;
}
.box1d {
  grid-area: box1d;
}
.sec {
  display: grid;
  grid-template-columns: 200px;
  grid-template-rows: 120px 120px;
  gap: 0px 0px;
  grid-template-areas:
    "box2A"
    "box2B";
  grid-area: sec;
}
.box2A {
  grid-area: box2A;
}
.box2B {
  grid-area: box2B;
}
.box1a,
.box1b,
.box1c,
.box1d,
.box2A,
.box2B {
  margin: 5px;
  border-radius: 10px;
  background: rgb(104, 101, 101);
  transition: 0.5s;
  cursor: pointer;
  border: 1px solid rgb(46, 46, 46);
}
/* .box1d:hover {
  background: rgb(93, 106, 119);
  box-shadow: 5px 5px 10px rgb(65, 65, 65);
  transform: translate(-20px, 20px);
  transition: 0.5s;
} */
/* :where(.box1a, .box1b, .box1c, .box1d, .box2A, .box2B):hover {
  background: rgb(93, 106, 119);
  box-shadow: 5px 5px 10px rgb(65, 65, 65);
  transform: translate(-20px, 20px) scale(1.05);
  transition: 0.5s;
} */
:where(.box1a, .box1b, .box1c, .box1d, .box2A, .box2B):hover {
  background: rgb(0, 74, 148);
  box-shadow: -5px -5px 5px 5px 10px rgb(110, 0, 138);
  transform: scale(1.1);
  transition: 0.3s;
}
.box2A:hover {
  transform: translate(21px, -20px) scale(0.9);
}
</style>
