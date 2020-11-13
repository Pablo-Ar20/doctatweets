<template>
    <div>
        <button @click="eliminarPost">Eliminar</button>
    </div>
</template>

<script>
export default {
    name: "BotonEliminarPost",

    methods: {
        eliminar(){
            this.$emit("eventoeliminarpost")
        }
        
    },
    
}
</script>