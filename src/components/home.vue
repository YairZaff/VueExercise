<template>
<div id="home">
    <h1>Home</h1>
    <h3>Tips</h3><hr>
    <marquee direction="right" speed="120%"><b v-for="(tip,index) in tips.tips" :key="index" class="tip"> {{tip.tip}}</b></marquee><hr>
    <SelectedA :selected='false' :getArticle="getArticle" />
</div>

</template>
<script>
import json from './tips/tips.json'
import SelectedA from './articles/selectedArticles'
export default {
    props:{
        getArticle: Function
    },
    components:{
        SelectedA,
        
    },
    data(){
        return{
            tips:json
        }
    },
    methods:{
        
    }
}
</script>
<style scoped>
.tip{
    color:mediumorchid;
    padding: 0% 2%;
}
</style>