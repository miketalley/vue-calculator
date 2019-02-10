<template>
  <v-card dark color="red" @click="click">
    <v-card-text class="text-xs-center">
      <i class="fa fa-equals"></i>
    </v-card-text>
  </v-card>
</template>

<script>
  export default {
    props: [
			'click'
		]
  }
</script>
