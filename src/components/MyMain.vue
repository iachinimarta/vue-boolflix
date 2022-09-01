<template>
    <main class="d-flex">
        <div class="welcome" v-show="rispostaApiFilm.length == 0">
            WELCOME!
        </div>  
        <div class="component-container">
            <MyCollection :rispostaApiFilm="rispostaApiFilm" :rispostaApiSerieTv="rispostaApiSerieTv"/> 
        </div>
                            
    </main>  
</template>

<script>
import MyCollection from './MyCollection.vue';
 
    export default {
        name: 'MyMain',
        components: {
            MyCollection
        },
        props: {
            rispostaApiFilm: Array,
            rispostaApiSerieTv: Array,
        },
    }
</script>

<style lang="scss">

    main {
        background-color: grey;
        margin-top: 80px;
        position: relative;

        .welcome {
            color: red;
            font-weight: bold;
            font-size: 5rem;
            position: absolute;
            top: calc(50vh - 70px);
            left: 50%;
            transform: translate(-50%);
        }
        
        .component-container {
            width: 90%;
            margin: auto;
        }
    }

</style>