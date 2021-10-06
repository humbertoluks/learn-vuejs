<template>
  <div class="row">

    <!-- coluna 1 -->
    <div class="col-8">

      <h2>Filmes</h2>

      <div class="list-group list-group-flush">
        
        <FilmesListaIten
            @selecionarFilme = "filmeSelecionado = $event"
            v-for = "filme in filmes"
            :key = "filme.Id"
            :filme = "filme"
            :class = "aplicarClasseActiva(filme)"
        />

      </div>
    </div>

    <!-- coluna 2 -->
    <div class="col-4">

      <FilmesListaItenInfo :filme="filmeSelecionado"/>

    </div>

  </div>
</template>

<script>

import FilmesListaIten from './FilmesListaIten.vue'
import FilmesListaItenInfo from './FilmesListaItenInfo.vue'

export default {
  components: {
    FilmesListaIten,
    FilmesListaItenInfo
  },
  data() {
    return {
        filmes: [
            {Id: 1, Titulo: 'Vingadores: Guerra Infinita', Ano: 2019},
            {Id: 2, Titulo: 'Homem Formiga e Vespa', Ano: 2019},
            {Id: 3, Titulo: 'Pantera Negra', Ano: 2019},
            {Id: 4, Titulo: 'Dead Pool 2', Ano: 2019}
        ],
        filmeSelecionado: undefined
    }
  },
  methods: {
      aplicarClasseActiva(filmeIterado) {
          return { active: this.filmeSelecionado && this.filmeSelecionado.Id === filmeIterado.Id}
      }
  }

}
</script>
