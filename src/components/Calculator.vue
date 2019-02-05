<template>
  <v-container fluid>

    <v-layout row text-xs-right justify-center>
      <v-flex xs4>
        <v-card>
          <v-card-text>
            {{ value }}
          </v-card-text>
        </v-card>
      </v-flex>
    </v-layout>
    
    <v-layout row justify-center>

      <v-flex xs3>
        <v-layout align-center justify-center column fill-height>
          <v-layout text-xs-center justify-center>
            <v-flex xs12>  
              <v-layout row wrap grid-list-xs>
                <v-flex v-for="num in numbers" :key="num" xs4>
                  <v-card>
                    <v-card-text>
                      {{ num }}
                    </v-card-text>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
        </v-layout> 
      </v-flex>

      <v-flex xs1>
        <v-layout column>
          <v-flex v-for="operator in operators" :key="operator">
            <v-card dark color="primary">
              <v-card-text class="text-xs-center">
                <i class="fa" :class="`fa-${operator}`"></i>
              </v-card-text>
            </v-card>
          </v-flex>
        </v-layout>
      </v-flex>

    </v-layout>

  </v-container>
</template>

<script>
  export default {
    data: () => {
      return {
        value: 0,
        currentOperator: null,
        appliedValue: [],
        numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
        operators: [
          'plus',
          'minus',
          'asterisk',
          'divide'
        ]
      };
    },
    computed: {
      enteredValue: () => {
        return this.appliedValue.join();
      }
    }
  }
</script>

<style>

</style>
