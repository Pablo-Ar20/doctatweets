<template>
    <div>
        <post v-for="(post,key) in posts" ::key="key">
        </post>
    </div>    
</template>

<script>
import Post from "./components/Post"
export default {
    name: "ListaPost",
    components:{
        Post,
    }
    
   created(){
        fetch("https://node-api-doctadevs.vercel.app/posts")
        .then(response => response.json())
        .then(result => {
            if(result.error) return console.log(result);
            this.posts = result.body;
            return true;
        })
        .catch(error => console.log(error));
    },
    data (){
        return{
            posts:[],
        }
    }
</script>