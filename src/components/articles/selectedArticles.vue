<template>
    <div>
        <!--{{articles}}-->
        <ArticlePreview v-for="(art,index) in articles.articles" :key="index"  :article="art" @selected-article="getArticle" />
    </div>
</template>
<script>
import json from './articles.json'
import ArticlePreview from './articlePreview'
export default {
    //name:"selectedComponents",
    props:{
        selected: Boolean,
        getArticle: Function
    },
    components:{
        ArticlePreview
    },
    data(){
        let tmp = {articles:[]};
        if(this.selected)
        {
            tmp.articles = json.articles.filter( art => art.selected)
        }
        else
        {
            tmp = json;
        }
        
        return{
            
            articles:tmp
        }
    },
    

}
</script>
<style scoped>

</style>