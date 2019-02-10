<template>
<v-card dark color="red" @click="click">
  <v-card-text class="text-xs-center">
    <i class="fa fa-equals"></i>
  </v-card-text>
</v-card>
</template>

<script>
const KEY_CODE = 187;
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
