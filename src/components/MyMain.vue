<template>
    <main class="d-flex">
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
@import './styles/Common.scss';

    main {
        background-color: grey;
        height: calc(100% - 80px);
        margin-top: 80px;
        
        .component-container {
            width: 90%;
            margin: auto;
        }
    }

</style>