<template>
    <li class="list-group-item">
        <span>{{ filme.Titulo }}</span>
        <button @click="selecionar" class="btn btn-secondary float-right">Selecionar</button>
    </li>
</template>

<script>
export default {
    props:{
        filme: {
            type: Object,
            require: true
        }
    },
    methods: {
        selecionar(){
           this.$emit('selecionarFilme', this.filme)
        }
    }
}
</script>

