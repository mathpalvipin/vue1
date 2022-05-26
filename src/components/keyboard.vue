<template>
  <div class="app">

    <div class="keyboard"  >
      <div class="controller">
    <div class="control" >
      <div class="heading"> Controller</div>
      <div class="control-keys">
      <p> <i class="arrow up" @click="changecolor(0)"></i></p>
      <p><i class="arrow right" @click="changecolor(1)"></i></p>
      <p> <i class="arrow down" @click="changecolor(2)"></i></p>
      <p><i class="arrow left" @click="changecolor(3)"></i></p>
    </div>
    </div>
    <div class="selector">
      <div class="heading "> Selector </div>
      <div class="selector-keys" >
      <p><i class="arrow up" @click="selector(0)"></i></p>
      <p><i class="arrow right" @click="selector(1)"></i></p>
      <p><i class="arrow down" @click="selector(3)"></i></p>
      <p> <i class="arrow left" @click="selector(2)"></i></p>
    </div>
  </div>
  </div>
      <div class="body">
        <div class="keyrow" v-for="item in items">
          <div
            class="key"
            v-for="i in item"
            v-bind:style="{ 'background-color': i.color }"
          >
            <div class="element" v-for="t in i.array">{{ t }}</div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
   import {store} from '../store.js'
export default {
   data() {
    return {
     
      items: [],
      letters: [
        "a",
        "b",
        "c",
        "d",
        "e",
        "f",
        "g",
        "h",
        "i",
        "j",
        "k",
        "l",
        "m",
        "n",
        "o",
        "p",
        "q",
        "r",
        "s",
        "t",
        "u",
        "v",
        "w",
        "x",
        "y",
        "z",
        "A",
        "B",
        "C",
        "D",
        "E",
        "F",
        "G",
        "H",
        "I",
        "J",
        "K",
        "L",

        "M",
        "N",
        "O",
        "P",
        "Q",
        "R",
        "S",
        "T",
        "U",
        "V",
        "W",
        "X",
        "Y",
        "Z",
        "0",
        "1",
        "2",
        "3",
        "4",
        "5",
        "6",
        "7",
        "8",
        "9",
        "@",
        "!", //,
        // "$",
        // "#",
      ],
      colors: [
        "#000000",
        "#00FFFF",
        "#8A2BE2",
        "#0000FF",
        "#A52A2A",
        "#00008B",
        "#A9A9A9",
        "#006400",
        "#FF1493",
        "#FFD700",
        "#90EE90",
        "#FF0000",
        "#F5F5F5",
        "#FFA500",
        "#D2B48C",
        "#20B2AA",
      ],
    };
  },
  mounted(){
    this.init();
  },
  methods: {
    init() {
      let randomAlgo = Math.floor(Math.random() * 2 + 1);
      console.log(randomAlgo);
      switch (randomAlgo) {
        case 1:
          // console.log("The Fisher-Yates algorith");
          for (let i = this.letters.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            const temp = this.letters[i];
            this.letters[i] = this.letters[j];
            this.letters[j] = temp;
          }
          for (let i = this.colors.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            const temp = this.colors[i];
            this.colors[i] = this.colors[j];
            this.colors[j] = temp;
          }
          break;
        case 2:
          // console.log("Simple algo ");
          this.letters = this.letters.sort((a, b) => 0.5 - Math.random());
          this.colors = this.colors.sort((a, b) => 0.5 - Math.random());
          break;
      }
      let n = 4;
      let m = 4;
      let count = 0;
      let colorcount = 0;
      for (let i = 0; i < n; i++) {
        let vr = [];
        for (let j = 0; j < m; j++) {
          let ar = [];
          for (let k = 0; k < 4; k++) {
            // console.log(i*n+j*m+k);
            ar[k] = this.letters[count++];
          }
          vr[j] = { array: ar, color: this.colors[colorcount++] };
        }

        this.items[i] = vr;
      }
    },
    changecolor(n) {
      console.log(n);
      let colors = this.colors;
      let rotation = 0;
      switch (n) {
        case 0:
          // console.log("up arroa");
          rotation = 4;

          this.colors = colors
            .slice(rotation)
            .concat(colors.slice(0, rotation));

          break;
        case 1:
          // console.log("right shift");
          rotation = 1;

          this.colors = colors
            .slice(0, 16 - rotation)
            .reverse()
            .concat(colors.slice(16 - rotation).reverse())
            .reverse();

          break;
        case 2:
          // console.log("up arrow");
          rotation = 4;

          this.colors = colors
            .slice(0, 16 - rotation)
            .reverse()
            .concat(colors.slice(16 - rotation).reverse())
            .reverse();

          break;
        case 3:
          // console.log("left arrow");
          rotation = 1;

          this.colors = colors
            .slice(rotation)
            .concat(colors.slice(0, rotation));

          break;
      }

      for (let i = 0; i < 4; i++) {
        for (let j = 0; j < 4; j++) {
          // console.log(this.items[i][j].color);
          // console.log(i*4+j);
          this.items[i][j].color = this.colors[i * 4 + j];
        }
      }
    },
    selector(n) {
      const color = "#A9A9A9";
      // let i= this.colors.find(color);

      //          var result = this.items.filter(obj => {
      //        const key= obj.filter(ob=>{
      //         console.log(ob.color+ color);
      //           return ob.color===color;
      //         })
      //         console.log(key[0]);
      //   return key[0];
      // })

      // console.log(result[0]);

      var key;
      for (let i = 0; i < 4; i++) {
        // console.log(this.items[i]);
        for (let j = 0; j < 4; j++) {
          // console.log(this.items[i][j]);
          if (this.items[i][j].color === color) {
            key = this.items[i][j];
          }
        }
      }
      // console.log(key.array[n]);

      var letter = key.array[n];
      // switch (n) {
      //   case 0:
      //     console.log("up left");

      //     break;
      //   case 1:
      //     console.log("up right ");

      //     break;
      //   case 2:
      //     console.log("down left");

      //     break;
      //   case 3:
      //     console.log("down right");

      //     break;
      // }

       
    store.password+=letter;
   
      this.init();
    },
  },
};
</script>
<style scoped>
.body {
  width: 100%;
  height: 100%;

  display: flex;
  flex-direction: column;
  justify-content: space-around;

  background-color: grey;
}
.keyrow {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  height: 20%;
}
.key {
  position: relative;
  width: 10%;
  border: 0.5px solid;
  background-color: lightblue;
  border-radius: 25%;
}
.element:nth-child(1) {
  position: absolute;
  top: -0.3vw;
  left: 0.5vw;
}
.element:nth-child(2) {
  position: absolute;
  top: -0.3vw;
  right: 0.5vw;
}
.element:nth-child(3) {
  position: absolute;
  bottom: -0.1vw;
  left: 0.5vw;
}
.element:nth-child(4) {
  position: absolute;
  bottom: -0.1vw;
  right: 0.5vw;
}
.element {
  font-size: clamp(15px, 2vw, 25px);
}
.keyboard {
  bottom: 10vh;
  width: clamp(600px,75vw, 1200px);
  height: clamp(200px, 30vw, 350px);
  border: 1px solid;
  position: absolute;
  display: flex;
  flex-direction: row;
}
.app {
  display: flex;

  justify-content: center;
}


.controller{
  display: flex;
  flex-direction: column;
  width: 30%;

}
.selector,.control{
  height: 50%;
  border: 1px solid black;
display: flex;
flex-direction: column;
position: relative;
}
.control-keys{
display: flex;
justify-content: center;
height: 100%;
align-items: center;
position: relative;
}

.arrow {
  border:  solid black;
  border-width: 0 3px 3px 0;
  display: inline-block;
  padding: 3px;
   position: absolute;
}


.control-keys .right {
  transform: rotate(-45deg);
  -webkit-transform: rotate(-45deg);
right: 30%;
top: 45%;
}

.control-keys .left {
  transform: rotate(135deg);
  -webkit-transform: rotate(135deg);
    left: 25%;
  top: 45%;
 
}

.control-keys .up {
   transform: rotate(-135deg);
  -webkit-transform: rotate(-135deg);
   left: 45%;
  top:20%;
}

.control-keys .down {
  transform: rotate(45deg);
  -webkit-transform: rotate(45deg);
   bottom: 20%;
  left: 45%;
}
 
 .selector-keys{
display: flex;
justify-content: center;
height: 100%;
align-items: center;
position: relative;
}

.selector-keys .right {
  transform: rotate(-90deg);
  -webkit-transform: rotate(-90deg);
right: 30%;
top: 30%;
}

.selector-keys .left {
  transform: rotate(90deg);
  -webkit-transform: rotate(90deg);
    left: 25%;
  bottom: 20%;
 
}

.selector-keys .up {
   transform: rotate(175deg);
  -webkit-transform: rotate(175deg);
   left: 25%;
  top:30%;
}

.selector-keys .down {
  transform: rotate(0deg);
  -webkit-transform: rotate(0deg);
   bottom: 20%;
  right: 30%;
}
 
.heading {
align-self: center;
}
</style>
