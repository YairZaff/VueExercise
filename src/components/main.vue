<template>
    
    <div id="navbar">
        <h1>Clean Info.</h1>
        <hr>
            <a href="#" @click="changePage(true)" :class = "home ? 'current' : 'none' ">Home</a> <a href="#"  @click="changePage(false)" :class = "!home ? 'current' : 'none'" >Search</a>
        <hr>
        <Home v-if="this.home" :getArticle="loadArticle" />
        <Search v-else :getArticle="loadArticle" />
        <div v-if="this.showArt">
            <ArticleViewer :article="loadedArt" @stop-show="showArticle(false)" :getArticle="loadArticle" />
        </div>
    </div>
</template>

<script>
import Home from './home'
import Search from './search'
import ArticleViewer from './articles/articleViewer'
export default {
    data(){
        return{
            home: true,
            current: 'current',
            none: 'none',
            showArt: false,
            loadedArt: {"title":"shouldnt see this","date":"01/01/2111", "selected":false, "content":"A place Holder"}
        };
    },
    methods:{
        changePage(bool){
            this.home=bool;
        },
        showArticle(bool){
            this.showArt = bool;
        },
        loadArticle(art){
            this.loadedArt=art;
            this.showArticle(true)
        }
    },
    components:{
        Home,
        Search,
        ArticleViewer
    }

    
}
</script>

<style scoped>
h1{
    color: rgb(40, 40, 40);
    padding: 0% 2% ;
}
hr{
    height: 2px;
    background-color: rgb(80, 80, 80) ;
}

.none{
    color: blue;
}
.current{
    color:green;
}
a{
    font-size: 200%;
    padding: 2% 2% ;
}


</style>
