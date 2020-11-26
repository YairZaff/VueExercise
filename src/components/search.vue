<template>
    <div>
        <h1>Search</h1>
        <input type="text" placeholder="search . . ." :value="this.search_queary" @input="getSearch"/>
        <!--<p>{{this.search_queary}}</p>-->
        <br>
        <h2 v-if="tip_results.tips.length!==0">tips:</h2>
        <div v-for="(tip,index) in tip_results.tips" :key=100+index><i><b> {{tip.tip}} </b></i></div>
        <ArticlePreview v-for="(art,index) in articles_results.articles" :key="index"  :article="art" @selected-article="getArticle" />
        
        
    </div>
    
</template>
<script>
import tipsjson from './tips/tips.json'
import articlejson from './articles/articles.json'
import ArticlePreview from './articles/articlePreview'
export default {
    data(){
        return{
            search_queary:"",
            tips:tipsjson,
            articles:articlejson,
            articles_results:{articles:[]},
            tip_results:{tips:[]}
        }
    },
    methods:{
        getSearch(event){
            this.search_queary=event.target.value;
            if(this.search_queary!=="")
            {
                this.articles_results.articles = this.articles.articles.filter( art => art.content.includes(this.search_queary) || art.title.includes(this.search_queary));
                this.tip_results.tips = this.tips.tips.filter(tip => tip.tip.includes(this.search_queary))
            }
            else
            {
                this.articles_results.articles =[];
                 this.tip_results.tips =[];
            }
        }
    },
    components:{
        ArticlePreview
    },
    props:{
        getArticle: Function
    }

}
</script>
<style scoped>
i{
    
}
</style>