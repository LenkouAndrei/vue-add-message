<template>
    <div class="row">
	    <app-single-quote v-for="(quote,index) in quotes" :key="index" :number="index">
		    <div :class="[(index === 0) ? 'defaultQuote' : '', 'quote']">{{ quote }}</div>
	    </app-single-quote>
    </div>
</template>

<script>
	import SingleQuote from './SingleQuote.vue';

    export default {
    	props: ['quotes'],
    	components: {
    		appSingleQuote: SingleQuote
    	}
    }
</script>

<style scoped>

</style>
