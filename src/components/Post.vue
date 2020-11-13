<template>
    <div>
        <div>
            <h3>{{autor}}</h3>
            <p>{{fecha}}</p>
            <p>{{mensaje}}</p>
            <boton-like @eventolike= "like">{{like}}</boton-like>
            <boton-eliminar-post @eventoeliminarpost= "eliminarPost"></boton-eliminar-post>
        </div>
    </div>    
</template>

<script>
import BotonLike from "./BotonLike";
import BotonEliminarPost from ".components/BotonEliminarPost";


export default {
    name: "Post",
    components:{
        BotonLike,
        BotonEliminarPost,
    };
    data() {
        return {
            post:{},
        }
    },
    props:{
        autor: String,
        fecha: Date,
        mensaje: String,
        likes: Number
    },
    methods: {
        like(){
        fetch("https://node-api-doctadevs.vercel.app/posts/{{POST_ID}}/like", {
                method: 'POST',
              })
             .then(response => response.text())
             .then(result => console.log(result))

             .catch(error => console.log('error', error));
        }
        
        eliminarPost(){
            fetch("https://node-api-doctadevs.vercel.app/posts/{{POST_ID}}")
            .then(response => response.text())
            .then(result => console.log(result))
            .catch(error => console.log('error', error));
        }
        
    },    
}
</script>