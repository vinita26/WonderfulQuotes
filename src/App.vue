<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <new-quote @quoteAdded="addNewQuote" ></new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteCurrentQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on quote box to delete it!</div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuotesGrid.vue'
    import NewQuote from './components/NewQuote.vue'
    import Header from './components/Header.vue'
    export default {
        data: function(){
            return {
                maxQuotes: 10,
                quotes: [
                    'Just a Quote to see something'
                ]
            }
        },
        methods: {
            addNewQuote(quote){
                if(this.quotes.length>=this.maxQuotes){
                    return alert('Please delete quote first');
                }
                this.quotes.push(quote);
            },
            deleteCurrentQuote(index){
                this.quotes.splice(index,1);
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            newQuote: NewQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>
