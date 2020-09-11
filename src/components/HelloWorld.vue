<template>
  <div class="hello">
    <div class="tambola">
      <div class="pick">
        <button @click="pickNumber" :disabled="isFinished" type="button">
          PICK
        </button>
        <button @click="isarray" :disabled="isFinished" type="button">
          Generate Ticket
        </button>

        <div class="current" v-text="currentNumber"></div>
      </div>
      <div class="board" :class="{ 'board-finished': isFinished }">
        <div class="number-box" v-for="n in boardNumbers" >
          <input
            disabled
            :checked="isChecked(n)"
            type="checkbox"
            :id="`number-${n}`"
          />
          <label :for="`number-${n}`">{{ n }}</label>
        </div>
      </div>
    </div>
    <h3>TICKETS</h3>
    <b-container class="bv-example-row jumbotron">
      <b-row v-for="n in array" >
        <b-col :for="`number-${n}`" cols="9"> {{ n }} </b-col>
      </b-row>

    </b-container>
  </div>
</template>

<script>
import tambola from "tambola-generator";
export default {
  name: "Tambola",
  props: {
    msg: String,
  },

  data() {
    return {
      boardNumbers: 90,
      array: [],
      checked: [],
      currentNumber: 0,
      _drawNumbers: [],
      checked2: [],
      currentNumber2: 0
    };
  },
  computed: {
    isFinished: function isFinished() {
      return this.checked.length === 90;
      // this.getTickets)
    },
  },
  methods: {
    isChecked: function isChecked(n) {
      return this.checked.includes(n);
    },
    isarray() {
      // var space = JSON.parse();
      var count = 1;
      var array = [
        [0, 0, 0, 0, 0, 0, 0, 0, 0],
          [0, 0, 4, 0, 0, 0, 0, 0, 0],
          [0, 0, 0, 0, 0, 0, 0, 0, 0],
        ];
        var arr1 = [1,2,3,4,5,6,7,8,9,10],
        arr2 = [11,12,13,14,15,16,17,18,19,20],
        arr3 = [21,22,23,24,25,26,27,28,29,30],
        arr4 = [31,32,33,34,35,36,37,38,39,40],
        arr5 = [41,42,43,44,45,46,47,48,49,50],
        arr6 = [51,52,53,54,55,56,57,58,59,60],
        arr7 = [61,62,63,64,65,66,67,68,69,70],
        arr8 = [71,72,73,74,75,76,77,78,79,80],
        arr9 = [81,82,83,84,85,86,87,88,89,90];
      for (var i = 0; i < 3; i++) {
      for(var j = 0; j < 9; j++)
      {
        if(j == 0){
          var temp = Math.floor(Math.random() * (arr1.length) + 0);
          array[i][j] = arr1[temp];
          arr1.splice(temp, 1);
        }
        
        else if(j == 1)
        {
         var temp = Math.floor(Math.random() * (arr2.length) + 0);
          array[i][j] = arr2[temp];
          arr2.splice(temp, 1);
        }
        else if(j == 2)
        {
          var temp = Math.floor(Math.random() * (arr3.length) + 0);
          array[i][j] = arr3[temp];
          arr3.splice(temp, 1);
        }
        else if(j == 3)
        {
          var temp = Math.floor(Math.random() * (arr4.length) + 0);
          array[i][j] = arr4[temp];
          arr4.splice(temp, 1);
        }
        else if(j == 4)
        {
          var temp = Math.floor(Math.random() * (arr5.length) + 0);
          array[i][j] = arr5[temp];
          arr5.splice(temp, 1);
        }
        else if(j == 5)
        {
         var temp = Math.floor(Math.random() * (arr6.length) + 0);
          array[i][j] = arr6[temp];
          arr6.splice(temp, 1);
        }
        else if(j == 6)
        {
         var temp = Math.floor(Math.random() * (arr7.length) + 0);
          array[i][j] = arr7[temp];
          arr7.splice(temp, 1);
        }
        else if(j == 7)
        {
          var temp = Math.floor(Math.random() * (arr8.length) + 0);
          array[i][j] = arr8[temp];
          arr8.splice(temp, 1);
        }
        else
        {
          var temp = Math.floor(Math.random() * (arr9.length) + 0);
          array[i][j] = arr9[temp];
          arr9.splice(temp, 1);
        }
        
      }
      this.array = array;

        // console.log("thh", this.array, Math.floor(Math.random()))
         this.array = array;
        //  this.array.push(array);
      }
      for(var i = 0; i < 3; i++)
      {
        for(var j = 0; j < 4; j++) {
          var arrtemp = [0,1,2,3,4,5,6,7,8,9];
          
        var remove =  Math.floor(Math.random() * (arrtemp.length) );
        console.log("remove", this.array[i][remove]);
        this.array[i][remove] = ' '.replace(/(^"|"$)/g, '');;
        arrtemp.splice(remove, 1); //delete value
        console.log(this.array[i][remove]);
        }
      }
      
    // }
    // return this.array;
      console.log("thh", this.array);
      
    },
    pickNumber: function pickNumber() {
      var number1 ;
      while (1) {
        var number = Math.ceil(Math.random() * this.boardNumbers);
        console.log("NUMBER", number);
        number1 = number;
        //  var number2 = Math.ceil(Math.random() * this.array);
        if (!this.checked.includes(number)) {
          this.checked.push(number);
          this.currentNumber = number;
          break;
        }
      }

      for(var i = 0; i<3;i++){
        for(var j= 0; j< 9; j++)
        {
          if(this.array[i][j] == number1)
          console.log("FOUND");
        }
      }
      
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  counter-reset: numbers;
  background: #16a085;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  display: flex;
  min-height: 100vh;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.bv-example-row{
  font-size: 44px;
}
.twitter-button {
  position: absolute;
  right: 1rem;
  top: 1rem;
}
input[type="checkbox"] {
  position: absolute;
  text-indent: -9999px;
  opacity: 0;
}
.tambola {
  display: grid;
  grid-template-areas:
    "pick board"
    "count count";
  grid-gap: 1rem;
}
.board {
  grid-area: board;
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  margin: auto;
  order: 2;
  border-radius: 10px !important;
  background: rgba(0, 0, 0, 0.3);
  padding: 1rem;
  justify-content: center;
  position: relative;
}
.board::after {
  opacity: 0;
  transition: 0.3s;
  content: "GAME OVER";
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  left: 0;
  top: 0;
  bottom: 0;
  right: 0;
  z-index: 1;
  background: rgba(255, 255, 255, 0.5);
  font-size: 10vh;
  color: rgb(200, 0, 0);
  text-shadow: 1px 1px rgb(150, 0, 0), 2px 2px rgb(150, 0, 0),
    3px 3px rgb(150, 0, 0), 4px 4px rgb(150, 0, 0);
}
.board-finished::after {
  opacity: 1;
}
.number-box {
  display: flex;
}
.number-box label {
  display: flex;
  flex: 1;
  justify-content: center;
  align-items: center;
  font-size: 4vh;
  color: white;
  background: #f1c40f;
  border-radius: 50%;
  -webkit-transform: scale(0.8);
  transform: scale(0.8);
  transition: 1s;
  transition-timing-function: cubic-bezier(0.86, -0.41, 0.38, 1.48);
  position: relative;
  height: 8vh;
  width: 8vh;
}
.number-box input:checked {
  counter-increment: numbers;
}
.number-box label::before {
  position: absolute;
  content: "";
  left: 0;
  top: calc(50% - 0.5vh);
  height: 1vh;
  width: 0;
  background: rgba(200, 0, 0, 0.5);
  transition: 0.3s;
}
.number-box label::after {
  -webkit-transform: rotate(90deg);
  transform: rotate(90deg);
}
.number-box input:checked + label {
  background: #2ecc71;
  -webkit-transform: scale(1);
  transform: scale(1);
  font-weight: bold;
}
.number-box input:checked + label::before {
  width: 100%;
}
.count {
  position: relative;
  order: 1;
  color: white;
  font-size: 1.5rem;
  font-weight: 100;
  grid-area: count;
  background: rgba(0, 0, 0, 0.3);
  padding: 1rem;
}
.count::after {
  content: counter(numbers);
}

.pick {
  grid-area: pick;
  min-width: 160px;
  background: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  flex-direction: column;
}
.pick button {
  font-size: 2rem;
  padding: 0.5rem 1rem;
  border-width: 1rem;
  border-color: #16a085;
  background: none;
  color: #fff;
  width: 100%;
  outline: none;
  position: relative;
}
.current {
  display: flex;
  padding: 2rem;
  color: #16a085;
  font-size: 3rem;
  background: rgba(0, 0, 0, 0.5);
  justify-content: center;
}

@media screen and (max-width: 480px) {
  .tambola {
    grid-template-areas:
      "pick"
      "count"
      "board";
  }
  .board {
    grid-template-columns: repeat(10, 1fr);
  }
  .number-box label {
    width: 5vh;
    height: 5vh;
    font-size: 2.5vh;
    font-weight: bold;
  }
}
</style>
