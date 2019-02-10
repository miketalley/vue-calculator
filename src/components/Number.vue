<template>
<v-card dark color="black" @click="click(num)">
  <v-card-text>
      {{ num }}
  </v-card-text>
</v-card>
</template>

<script>
const NUMBER_KEYCODES = {
  48: 0,
  49: 1,
  50: 2,
  51: 3,
  52: 4,
  53: 5,
  54: 6,
  55: 7,
  56: 8,
  57: 9
};

export default {
  props: [
    'num',
    'click'
  ],
  created() {
    document.addEventListener('keydown', (e) => {
      const recognizedKeyCode = NUMBER_KEYCODES[e.keyCode];

      if (recognizedKeyCode != this.num) {
        return;
      }

      this.click(this.num);
    });
  }
}
</script>
