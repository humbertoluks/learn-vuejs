<template>
    <li class="list-group-item">
        <span>{{ filme.Titulo }}</span>
        <button @click="selecionar" class="btn btn-secondary float-right">Selecionar</button>
    </li>
</template>

<script>
import { eventBus } from './../main'
export default {
    props:{
        filme: {
            type: Object,
            require: true
        }
    },
    methods: {
        selecionar(){
           eventBus.selecionarFilme(this.filme)
        }
    }
}
</script>

