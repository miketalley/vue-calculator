<template>
<v-card dark color="black" @click="click">
  <v-card-text class="text-xs-center">
    Clear
  </v-card-text>
</v-card>
</template>

<script>
const KEY_CODE = 27;
const SHIFT_KEY = false;

export default {
  props: [
    'click'
  ],
  created() {
    document.addEventListener('keydown', (e) => {
      const keyCodeMatch = e.keyCode == KEY_CODE;
      const shiftMatch = e.shiftKey === SHIFT_KEY;

      if (!shiftMatch || !keyCodeMatch) {
        return;
      }

      this.click();
    });
  }
}
</script>
