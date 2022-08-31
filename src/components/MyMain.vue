<template>
    <main class="d-flex">       
        <MyCollection :rispostaApiFilm="rispostaApiFilm" :rispostaApiSerieTv="rispostaApiSerieTv"/>                 
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
    }

</style>