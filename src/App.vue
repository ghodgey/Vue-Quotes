<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
                                    <!-- same as newQuote($event) or could add quotes.push($event)  -->
        <app-newquote @quoteAdded="newQuote"></app-newquote>
        <!-- I could say "quotes.splice($event, 1) but using a method - vue does it like deleteMyQuote($event) - dont need to pass event - vue does it for us" -->
        <app-quotegrid :quotes="quotes" @quoteDeleted="deleteMyQuote"></app-quotegrid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: CLick on a quote to delete it!</div>
            </div>
        </div>
    </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";



    
    export default {
        data: function()
        {
            return{
                quotes:[
                    'Just a default quote',
                    ],
                    maxQuotes: 10
                
            };
        },
        methods: {
            newQuote(quote)
            {
                if(this.quotes.length < this.maxQuotes) {
                    this.quotes.push(quote);

                } else {
                    return alert("You are only allowed 10 quotes! Please delete some");
                }
            },
            deleteMyQuote(index)
            {
                this.quotes.splice(index, 1)
            }
        },
        components:{
            "app-quotegrid": QuoteGrid,
            "app-newquote": NewQuote,
            "app-header": Header
        },
       
    }
</script>

<style scoped>
    
</style>
