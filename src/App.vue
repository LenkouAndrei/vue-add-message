<template>
    <div class="container">
		<app-status :amount="messages.length"></app-status>
	    <div class="row">
            <div class="col-xs-9 col-xs-offset-3">
                <div class="quotter">
                    <h2 class="quotter__headline">Quote</h2>
                    <textarea cols="120" rows="10" class="quotter__field" v-model="message"></textarea>
                    <div class="text-center margin-bottom">
                        <button class="btn btn-primary" @click="postQuote">Add Quote</button>
                    </div>
                </div>
            </div>
        </div>
        <app-quote-list :quotes="messages"></app-quote-list>
        <div>
            <div class="panel panel-info margin-top" v-if="infoPanel">
                <div class="panel-heading text-center">Info: Click on a Quote to delete it</div>
            </div>
            <div class="panel panel-danger margin-top" v-else>
                <div class="panel-heading text-center">Delete any qoute to write a new one</div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuotesList from './components/QuotesList.vue';
    import Status from './components/Status.vue';
    import { eventBus } from './main';

    export default {
        components: {
            appQuoteList: QuotesList,
            appStatus: Status
        },
        data() {
            return {
                infoPanel: true,
                message: '',
                messages: ["Just a Quote to abort with something!"]
            }
        },
        methods: {
            postQuote() {
                if(this.messages.length < 10) {
                    this.messages.push(this.message);
                    this.message = '';
                } else {
                    this.infoPanel = false
                }
            }
        },
        created() {
            eventBus.$on('messagesWasEdit', (number) => {
                this.messages.splice(number, 1);
                this.infoPanel = this.infoPanel || true;
            });
        }
    }
</script>

<style>
.margin-top {
    margin-top: 10px;
}
.margin-bottom{
    margin-bottom: 10px;
}
</style>
