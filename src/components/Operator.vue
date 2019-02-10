<template>
<v-card dark color="grey darken-3" @click="click(operator)">
  <v-card-text class="text-xs-center">
    <i class="fa" :class="`fa-${icon}`"></i>
  </v-card-text>
</v-card>
</template>

<script>
const OPERATOR_DATA = {
  '/': {
    icon: 'divide',
    keyCode: 191,
    shiftKey: false
  },
  '*': {
    icon: 'times',
    keyCode: 56,
    shiftKey: true
  },
  '-': {
    icon: 'minus',
    keyCode: 189,
    shiftKey: false
  },
  '+': {
    icon: 'plus',
    keyCode: 187,
    shiftKey: true
  }
};

export default {
  props: [
    'operator',
    'click'
  ],
  data() {
    return {
      icon: OPERATOR_DATA[this.operator].icon,
      keyCode: OPERATOR_DATA[this.operator].keyCode,
      shiftKey: OPERATOR_DATA[this.operator].shiftKey
    }
  },
  created() {
    document.addEventListener('keydown', (e) => {
      const keyCodeMatch = e.keyCode == this.keyCode;
      const shiftMatch = e.shiftKey === this.shiftKey;

      if (!shiftMatch || !keyCodeMatch) {
        return;
      }

      this.click(this.operator);
    });
  }
}
</script>
