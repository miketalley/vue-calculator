<template>
  <v-card dark color="black" @click="click(num)">
    <v-card-text>
        {{ num }}
    </v-card-text>
	</v-card>
</template>

<script>
  export default {
    props: [
			'num',
			'click'
		]
  }
</script>
