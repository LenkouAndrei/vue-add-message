<template>
    <div>
        <h1>Quotes Added</h1>
        <div class="progress-bar">
            <div class="progress-bar__background" :style="{width: grow}">
                <p class="progress-bar__text">{{ width }} / {{ maxLength }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                width: 1,
                maxLength: 10
            }
        },
        computed: {
            grow() {
                return (800 / this.maxLength) * this.width + 'px';
            }
        }
    }
</script>

<style scoped>
    .progress-bar{
        width: 800px;
        height: 20px;
        margin: 0 auto;
        position: relative;
        background: lightgray;
        border: 1px solid black;
        border-radius: 2px;
    }
    .progress-bar__background{
        position: absolute;
        left: 0;
        top: 0;
        height: 100%;
        background: blue;
    }
    .progress-bar__text{
        margin: auto;
        font-size: 15px;
        color: white;
    }
</style>
