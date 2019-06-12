<template>
    <div class="container">
        <app-header :quotesCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="NewQuote"></app-new-quote> 
        <app-quote-grid :quotes="quotes" @quoteDeleted= "deleteQuote"></app-quote-grid>
        <div class="row">
        <div class="col-sm-12 text-center">
        <div class="alert alert-info">Haz click en un quote para borrarlo</div>
        </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';

    export default {
        data: function(){
            return{
                quotes: [ 
                    'Hola mundo cruel',
                ],
                maxQuotes: 10
            }
        },
        methods:{
        NewQuote(quote){
                if(this.quotes.length >= this.maxQuotes){
                                    return alert("Borra algun quote para continuar")
                }
                    this.quotes.push(quote);
        },
        deleteQuote(index){
            this.quotes.splice(index, 1);
        }
    },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header,
        }
        
}
</script>

<style>
</style>
