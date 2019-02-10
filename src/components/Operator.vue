<template>
  <v-card dark color="grey darken-3" @click="click(operator)">
    <v-card-text class="text-xs-center">
      <i class="fa" :class="`fa-${operator}`"></i>
    </v-card-text>
  </v-card>
</template>

<script>
  export default {
    props: [
			'operator',
			'click'
		]
  }
</script>
