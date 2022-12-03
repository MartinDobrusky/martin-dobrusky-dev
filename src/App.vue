<script setup>
//import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <body>
    <div class="container">
      <h1 class="hello-text">Hi, I am</h1>
      <h1 class="main-name">MARTIN DOBRUSKÝ</h1>
      <h1 class="work-text">
        and I'm a
        <span class="typed-text">{{ typeValue }}</span>
        <span class="blinking-cursor">|</span>
        <span class="cursor" :class="{ typing: typeStatus }">&nbsp;</span>
      </h1>
      <div class="social">
        <div class="social-block">
          <a href="https://github.com/MartinDobrusky"><i class="fa fa-github"></i></a>
        </div>
        <div class="social-block">
          <a href="#"><i class="fa fa-facebook"></i></a>
        </div>
        <div class="social-block">
          <a href="#"><i class="fa fa-linkedin"></i></a>
        </div>
      </div>
      <div class="email">
        <div class="email-block">
          <p>martin@dobrusky.dev</p>
        </div>
      </div>
    </div>
  </body>
</template>

<script>
export default {
  name: "typeWiriter",
  data: () => {
    return {
      typeValue: "",
      typeStatus: false,
      displayTextArray: ["Indie Game Developer", "Developer", "Programmer", "Freelancer"],
      typingSpeed: 70,
      erasingSpeed: 90,
      newTextDelay: 2000,
      displayTextArrayIndex: 0,
      charIndex: 0,
    };
  },
  props: {},
  created() {
    setTimeout(this.typeText, this.newTextDelay + 200);
  },
  methods: {
    typeText() {
      if (this.charIndex < this.displayTextArray[this.displayTextArrayIndex].length) {
        if (!this.typeStatus) this.typeStatus = true;
        this.typeValue += this.displayTextArray[this.displayTextArrayIndex].charAt(
            this.charIndex
        );
        this.charIndex += 1;
        setTimeout(this.typeText, this.typingSpeed);
      } else {
        this.typeStatus = false;
        setTimeout(this.eraseText, this.newTextDelay);
      }
    },
    eraseText() {
      if (this.charIndex > 0) {
        if (!this.typeStatus) this.typeStatus = true;
        this.typeValue = this.displayTextArray[this.displayTextArrayIndex].substring(
            0,
            this.charIndex - 1
        );
        this.charIndex -= 1;
        setTimeout(this.eraseText, this.erasingSpeed);
      } else {
        this.typeStatus = false;
        this.displayTextArrayIndex += 1;
        if (this.displayTextArrayIndex >= this.displayTextArray.length)
          this.displayTextArrayIndex = 0;
        setTimeout(this.typeText, this.typingSpeed + 1000);
      }
    },
  },
};
</script>

<style scoped>
 body {
  font-family: "Varela Round", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: linear-gradient(320deg, #090c08, #090c08, #002a54);
  height: 100vh;
}

.hello-text{
  font-size: 3vw;
  color: rgb(253, 255, 252, 0.5);
}

.main-name{
  color: rgb(253, 255, 252);
  font-size: 5vw;
}

@media only screen and (max-width: 800px) {
  .hello-text{
    font-size: 5vw;
    color: rgb(253, 255, 252, 0.5);
  }

  .main-name{
    color: rgb(253, 255, 252);
    font-size: 8vw;
  }
}

.social {
  padding-top: 2vh;
}

.social-block:first-child {
  padding-left: 0;
}

.social-block{
  display: inline-block;
  padding-left: 20px;
}

.social a {
  font-family: "FontAwesome", sans-serif;
  font-style: normal;
  font-weight: normal;
  -webkit-font-smoothing: antialiased;
  line-height: 0;
  width: 40px;
  display: inline-block;
  position: relative;
  text-align: center;
  color: white;
  font-size: 40px;
  padding: 20px;
  cursor: pointer;
  background-color: rgba(0, 127, 255, 0.1);
  border-radius: 20% !important;
  transition: 0.5s;
  text-decoration: none;
}

.social a:hover {
  color: white;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 18% !important;
}

.email {
  padding-top: 2vh;
}

.email p {
  -webkit-font-smoothing: antialiased;
  line-height: 0;
  width: 240px;
  display: inline-block;
  position: relative;
  text-align: center;
  color: white;
  font-size: 20px;
  padding: 20px;
  cursor: pointer;
  background-color: rgba(0, 127, 255, 0.1);
  border-radius: 10px !important;
  transition: 0.5s;
  text-decoration: none;
}

.email p:hover {
  color: white;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 5px !important;
}

@media only screen and (max-width: 800px) {
  .social a {
    font-family: "FontAwesome", sans-serif;
    font-style: normal;
    font-weight: normal;
    -webkit-font-smoothing: antialiased;
    line-height: 0;
    width: 30px;
    display: inline-block;
    position: relative;
    text-align: center;
    color: white;
    font-size: 30px;
    padding: 20px;
    cursor: pointer;
    background-color: rgba(0, 127, 255, 0.6);
    border-radius: 20% !important;
    transition: 0.5s;
    text-decoration: none;
  }
}
</style>


<style scoped>
.container {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.work-text {
  color: rgb(253, 255, 252, 0.5);
  font-size: 3vw;
  font-weight: normal;
}

.blinking-cursor {
  font-size: 3vw;
  color: #2c3e50;
  -webkit-animation: 1s blink step-end infinite;
  -moz-animation: 1s blink step-end infinite;
  -ms-animation: 1s blink step-end infinite;
  -o-animation: 1s blink step-end infinite;
  animation: 1s blink step-end infinite;
}

@media only screen and (max-width: 800px) {
  .work-text {
    color: rgb(253, 255, 252, 0.5);
    font-size: 5vw;
    font-weight: normal;
  }

  .blinking-cursor {
    font-size: 5vw;
    color: #2c3e50;
    -webkit-animation: 1s blink step-end infinite;
    -moz-animation: 1s blink step-end infinite;
    -ms-animation: 1s blink step-end infinite;
    -o-animation: 1s blink step-end infinite;
    animation: 1s blink step-end infinite;
  }
}

span.typed-text {
  color: #007fff;
}

@keyframes blink {
  from,
  to {
    color: transparent;
  }
  50% {
    color: #2c3e50;
  }
}
@-moz-keyframes blink {
  from,
  to {
    color: transparent;
  }
  50% {
    color: #2c3e50;
  }
}
@-webkit-keyframes blink {
  from,
  to {
    color: transparent;
  }
  50% {
    color: #2c3e50;
  }
}
@-ms-keyframes blink {
  from,
  to {
    color: transparent;
  }
  50% {
    color: #2c3e50;
  }
}
@-o-keyframes blink {
  from,
  to {
    color: transparent;
  }
  50% {
    color: #2c3e50;
  }
}
</style>
