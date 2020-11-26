<template>
    <div>
        <div  class="preview" @click="$emit('selected-article',article)">
            <h2> {{ article.title}} </h2>
            <p>{{ previewText(article.content) }} <b>. . .<i> click to continue to read.</i></b></p>
            <h5>{{article.date}}</h5>
        </div>
       
    </div>
    
</template>

<script>

export default {
    props:{
        article: Object,
    },

    methods:{
       
        previewText(text){
            const presize=256;
            return (text.length < presize) ? text : text.slice(0,presize);
        }

    }
    

}
</script>

<style scoped>
div.preview{
    border-style: dashed;
    padding: 2% 2%;
    width: 30%;
    background-color: whitesmoke;
    margin: 2% 0%;
}
.preview h5{
    font-style: italic;
    color:teal
}
.preview b{
    color:mediumblue;
}

</style>