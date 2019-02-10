<template>
  <v-container fluid>

    <v-layout row wrap text-xs-right justify-center>
      <v-flex xs12 sm10 md4>
        <v-card dark color="grey darken-4">
          <v-card-text>
            {{ enteredValue || value }}
          </v-card-text>
        </v-card>
      </v-flex>
      <v-flex xs12 sm2 md1>
        <v-card dark color="black" @click="clear">
          <v-card-text class="text-xs-center">
            DEL
          </v-card-text>
        </v-card>
      </v-flex>
    </v-layout>

    <v-layout row wrap justify-center>
      <v-flex xs12 sm10 md4>
        <v-layout column align-space-around>
          <v-layout text-xs-center justify-center>
            <v-flex xs12>
              <v-layout row wrap grid-list-xs>
                <v-flex v-for="num in numbers" :key="num" xs4>
                  <Number :num="num" :click="numberClick"></Number>
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
        </v-layout>
      </v-flex>

      <v-flex xs12 sm2 md1>
        <v-layout column>
          <v-flex v-for="operator in operators" :key="operator">
            <v-card dark color="grey darken-3" @click="operatorClick(operator)">
              <v-card-text class="text-xs-center">
                <i class="fa" :class="`fa-${operator}`"></i>
              </v-card-text>
            </v-card>
          </v-flex>
          <v-card dark color="red" @click="equals">
            <v-card-text class="text-xs-center">
              <i class="fa fa-equals"></i>
            </v-card-text>
          </v-card>
        </v-layout>
      </v-flex>
    </v-layout>

  </v-container>
</template>

<script>
import Number from './Number.vue';
const MATH_OPERATORS = {
  divide: '/',
  times: '*',
  minus: '-',
  plus: '+'
};

export default {
  data: () => {
    return {
      value: 0,
      currentOperator: null,
      appliedValue: [],
      numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      operators: Object.keys(MATH_OPERATORS)
    };
  },
  methods: {
    numberClick(num) {
      this.appliedValue.push(num);
    },
    operatorClick(operator) {
      if (!this.value) {
        this.value = this.enteredValue;
        this.appliedValue = [];
      }
      this.currentOperator = MATH_OPERATORS[operator];
    },
    equals() {
      this.value = eval(`${this.value} ${this.currentOperator} ${this.enteredValue}`);
      this.currentOperator = null;
      this.appliedValue = [];
    },
    clear() {
      this.value = 0;
      this.currentOperator = null;
      this.appliedValue = [];
    }
  },
  computed: {
    enteredValue() {
      return this.appliedValue.join('');
    }
  },
  components: {
    Number
  }
};
</script>
