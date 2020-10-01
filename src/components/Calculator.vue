<template>
  <v-container>
    <v-row dense justify="center">
      <v-col cols="12" sm="8" lg="4" class="text-right">
        <v-sheet
          min-height="6"
          class="pr-6 pt-12 pb-3"
          color="cyan"
          dark
          elevation="3"
        >
          {{ display }}
        </v-sheet>
      </v-col>
    </v-row>
    <!-- Top row functions-->
    <v-row justify="center" dense>
      <v-col cols="3" sm="2" lg="1">
        <Operation button-color="red" operationValue="C" @clicked="clearScreen">
        </Operation>
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Operation button-color="red" @clicked="backspace">
          <v-icon color="grey darken-3" small>backspace</v-icon>
        </Operation>
      </v-col>
    </v-row>
    <!-- first row -->
    <v-row class="text-center" dense justify="center">
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="7" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="8" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="9" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Operation operationValue="X" @clicked="multiplication"/>
      </v-col>
    </v-row>
    <!-- second row -->
    <v-row class="text-center" dense justify="center">
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="4" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="5" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="6" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Operation operationValue="-" @clicked="subtraction"/>
      </v-col>
    </v-row>
    <!-- third row -->
    <v-row class="text-center" dense justify="center">
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="1" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="2" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="3" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Operation operationValue="+" @clicked="addition"/>
      </v-col>
    </v-row>
    <!-- fourth row -->
    <v-row class="text-center" dense justify="center">
      <v-col cols="3" sm="2" lg="1">
        <Operation operationValue="+/-" @clicked="signChange"/>
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="numericalClicked" numeralValue="0" />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Numeral @clicked="dotClicked" numeralValue="." />
      </v-col>
      <v-col cols="3" sm="2" lg="1">
        <Operation operationValue="=" @clicked="equals"/>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Numeral from "./Numeral";
import Operation from "./Operation";
export default {
  name: "HelloWorld",
  components: {
    Numeral,
    Operation,
  },
  data: () => ({
    prev: "",
    display: "0",
    operator: null,
    operatorPressed: false
  }),
  methods: {
    clearScreen() {
      this.display = "0";
      this.prev="";
      this.operator=null;
    },
    backspace() {
      // console.log('backspace pressed')
      if(this.display=='0') return;
      let length = this.display.length;
      if(length>1)
        this.display= this.display.substr(0, length - 1);
      else  this.display='0'
    },
    numericalClicked(num) {
      if(this.operatorPressed===true)
      {
          this.display=''+num;
          this.operatorPressed=false;
      }
      else
        this.display = this.display==='0' ? (''+num) : this.display+num;
    },
    dotClicked(){
        if(this.display.includes("."))  return;
        this.display= this.display+".";
    },
    signChange(){
      if(this.display.charAt(0)=='-')
          this.display=this.display.substr(1);
      else if(Number(this.display)!==0)
          this.display='-'+this.display;
    },
    operatorBasicFunction(operation){
        this.prev=this.display;
        this.operator=operation;
        this.operatorPressed=true;
    },
    addition(){
      this.operatorBasicFunction( (a,b)=> a+b);
    },
    subtraction(){
      console.log(this.prev+' '+this.display+' ')
      this.operatorBasicFunction( (a,b)=> a-b );
    },
    multiplication(){
      this.operatorBasicFunction( (a,b)=> a*b );
    },
    equals(){
        if(this.prev.length>0)
        {
          let result= this.operator(Number(this.prev),Number(this.display));
          console.log(this.prev+' '+this.display+' '+result)
           this.prev=this.display;
           this.display=''+result; 
        }
        else
        {
          console.log(this.prev+' '+this.display+' ')
          
        }
    }
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
}
.border {
  border: 1px solid black;
}
</style>
