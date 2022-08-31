<template>
    <main>
        <div>
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

</style>