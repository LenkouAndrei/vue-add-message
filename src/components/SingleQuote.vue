<template>
	<div class="col-xs-3" @click="showNumber()">
		<slot></slot>
	</div>
</template>

<script>
	import { eventBus } from './../main';

    export default {
    	props: ['number'],
    	methods: {
    		showNumber() {
    			if (this.number !== 0) {
    				eventBus.$emit('messagesWasEdit', this.number);
    			} else {
    				console.log("Can't remove");
    			}
    		}
    	}
    }
</script>

<style scoped>
	.quote{
		border: 1px solid gray;
		height: 50px;
		padding: 10px;
		margin: 5px 0;
		cursor: pointer;
	}
	.quote:hover {
		background: pink;
		transition-duration: .3s;
	}
	.defaultQuote{
		height: 110px;
	}
</style>