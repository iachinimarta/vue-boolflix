<template>
    <main>
        <div>
            <h1>Film</h1>
            <ol>
                <li v-for="(film, index) in rispostaApiFilm" :key="index">
                    <ul>
                        <li>Titolo: {{film.title}}</li>
                        <li>Titolo originale: {{film.original_title}}</li>
                        <li>Lingua: {{film.original_language}}</li>
                        <li>Voto: {{film.vote_average}}</li>
                    </ul>
                </li>
            </ol>
        </div>

        <div>
            <h1>Serie TV</h1>
            <ol>
                <li v-for="(serie, index) in rispostaApiSerieTv" :key="index">
                    {{serie.original_name}}
                </li>
            </ol>          
        </div>  
    </main>  
</template>

<script>
    export default {
        name: 'MyMain',
        props: {
            rispostaApiFilm: Array,
            rispostaApiSerieTv: Array
        }   
    }
</script>

<style lang="scss">

</style>