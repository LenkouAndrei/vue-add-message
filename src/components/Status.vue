<template>
    <div class="row">
		<h1>Quotes Added</h1>
		<div class="progress-bar">
			<div class="progress-bar__background" :style="{width: setLength}">
				<p class="progress-bar__text">{{ amount }} / {{ totalAmount }}</p>
			</div>
		</div>
    </div>
</template>

<script>
    export default {
    	props: ['amount'],
    	data() {
    		return {
    			totalAmount: 10
    		}
    	},
    	computed: {
    		setLength() {
    			return (1180 / 10) * this.amount + 'px';
    		}
    	}
    }
</script>

<style scoped>
	.progress-bar{
		width: 1180px;
		height: 20px;
		margin: 0 auto;
		background: lightgray;
		border: 1px solid gray;
		border-radius: 5px;
		position: relative;
	}
	.progress-bar__background{
		position: absolute;
		top: 0;
		left: 0;
		background: blue;
		width: 400px;
		height: 100%;
	}
	.progress-bar__text{
		margin: auto;
		font-size: 15px;
		color: white;
	}
</style>
