<template>
    <div>
        <div class="full">
            {{scrollToTop()}}
            <center>
            <div class="articlePage">
                <a href="#" @click="stopShow()" >Back.</a>
                <h1>{{ article.title}}</h1>
                <h2>{{article.date}}</h2>
                <img :src="image" />
                <p>{{ article.content}}</p>
                <SelectedA :selected='true' :getArticle="getArticle" />
            </div>
            </center>
        </div>
    </div>
</template>

<script>
import SelectedA from './selectedArticles'
export default {
    name:"art",
    components:{
        SelectedA
    },
    props:{
        article: Object,
        getArticle: Function
    },
    data(){
        return{
            //show:true,
            image: require("./"+this.article.imgsrc+".png")
        }
    },
    methods:{
       
        scrollToTop() {
                window.scrollTo(0,0);
        },
        stopShow(){
            //this.show=false;
            this.$emit('stop-show')
        },
        
    }
}
</script>

<style scoped>

div.full{
    z-index: 99;
    position: absolute;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.5);
    
    height: 100%;
    width: 100%;
    padding-bottom: 100%;
    
}
div.articlePage{
    background-color: white;
    margin: 5% 10%;
    padding: 2% 3%;
    text-align: left;
}
.articlePage p{
    font-size: 120%;
}
.articlePage h1{
    text-decoration: underline;
}
.articlePage a{
    font-size: 200% ;
    text-decoration: bold;
}
.articlePage a:visited{
    color: blue;
    
}
.articlePage img{
    height: 256px;
    width: 256px;
}
</style>