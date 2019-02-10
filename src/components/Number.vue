<template>
<v-card dark color="black" @click="click(num)">
  <v-card-text>
      {{ num }}
  </v-card-text>
</v-card>
</template>

<script>
const NUMBER_KEYCODES = {
  0: 48,
  1: 49,
  2: 50,
  3: 51,
  4: 52,
  5: 53,
  6: 54,
  7: 55,
  8: 56,
  9: 57
};

export default {
  props: [
    'num',
    'click'
  ],
  data() {
    return {
      keyCode: NUMBER_KEYCODES[this.num]
    }
  },
  created() {
    document.addEventListener('keydown', (e) => {
      const keyCodeMatch = e.keyCode == this.keyCode;

      if (e.shiftKey || !keyCodeMatch) {
        return;
      }

      this.click(this.num);
    });
  }
}
</script>
