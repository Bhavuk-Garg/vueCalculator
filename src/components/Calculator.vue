<template>
  <v-container>
    <v-row dense justify="center">
      <v-col cols="4" class="text-right">
        <v-sheet
          min-height="6"
          class="pr-6 pt-12 pb-3"
          color="cyan"
          dark
          elevation="3"
        >
          {{ expression }}
        </v-sheet>
      </v-col>
    </v-row>
    <!-- Top row functions-->
    <v-row justify="center" dense>
      <v-col cols="1">
        <Operation button-color="red" operationValue="C" @clicked="clearScreen">
        </Operation>
      </v-col>
      <v-col cols="1">
        <Operation button-color="red" @clicked="backspace">
          <v-icon color="grey darken-3" small>backspace</v-icon>
        </Operation>
      </v-col>
    </v-row>
    <!-- first row -->
    <v-row class="text-center" dense justify="center">
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="7" />
      </v-col>
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="8" />
      </v-col>
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="9" />
      </v-col>
      <v-col cols="1">
        <Operation operationValue="X" />
      </v-col>
    </v-row>
    <!-- second row -->
    <v-row class="text-center" dense justify="center">
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="4" />
      </v-col>
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="5" />
      </v-col>
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="6" />
      </v-col>
      <v-col cols="1">
        <Operation operationValue="-" />
      </v-col>
    </v-row>
    <!-- third row -->
    <v-row class="text-center" dense justify="center">
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="1" />
      </v-col>
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="2" />
      </v-col>
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="3" />
      </v-col>
      <v-col cols="1">
        <Operation operationValue="+" />
      </v-col>
    </v-row>
    <!-- fourth row -->
    <v-row class="text-center" dense justify="center">
      <v-col cols="1">
        <Operation operationValue="+/-" />
      </v-col>
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="0" />
      </v-col>
      <v-col cols="1">
        <Numeral @clicked="numericalClicked" numeralValue="." />
      </v-col>
      <v-col cols="1">
        <Operation operationValue="=" />
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
    expression: "0",
  }),
  methods: {
    clearScreen() {
      this.expression = "";
    },
    backspace() {
      let length = this.expression.length;
      this.expression = this.expression.substr(0, length - 1);
    },
    numericalClicked(num) {
      this.expression = this.expression + num;
    },
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
