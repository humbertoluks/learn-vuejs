<template>
    <div>
        <h2>Editar filme</h2>

        <div class="form-group">
            <label>Título:</label>
            <input 
                type="text" 
                class="form-control" 
                placeholder="Insira o título"
                :value="filmeSelecionado.titulo"
                @input="filmeSelecionado = { propriedade: 'titulo', valor: $event.target.value}">
                <!-- :value="filme.Titulo"> -->
        </div>

        <div class="form-group">
            <label>Título:</label>
            <input 
                type="text" 
                class="form-control" 
                placeholder="Insira o ano"
                :value="filmeSelecionado.ano"
                @input="filmeSelecionado = { propriedade: 'ano', valor: $event.target.value}">
                <!-- :value="filme.Ano"> -->
        </div>
        
         <button @click="salvarFilme" class="btn btn-primary float-right">Salvar</button>
         
    </div>
</template>

<script>

import { eventBus } from './../main'

export default {
    props:{
        filme: {
            Object,
            required: true
        }
    },
    data() {
        return {
            filmeLocal: this.filme
        }
    },
    computed: {
        filmeSelecionado: {
            set (dados) {
                this.filmeLocal = Object.assign(
                    {},
                    this.filmeLocal,
                    { [dados.propriedade]: dados.valor }
                )
            },
            get() {
                return this.filme
            }
        }
    },
    watch: {
        filme(novoFilme) { // crie o watcher na prop "filme"
            this.filmeLocal = Object.assign({}, novoFilme)
        }
    },
    methods: {
        salvarFilme() {
            // this.$emit('atualizarFilme', this.filmeLocal)
            eventBus.atualizarFilme(this.filmeLocal)
        }
    }
}
</script>