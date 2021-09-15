<template>
    <div class="container">
        <h1>Comentários</h1>
        <hr />
        <FormTodo v-on:add-todo="addComment"></FormTodo>
        <p v-if="comments.length <= 0">Sem comentários...</p>
        <div class="list-group">
            <div class="list-group-item" v-for="(comment, index) in allComments" :key="index">
                <span class="comment__author">Autor: <strong>{{ comment.name }}</strong></span>
                <p>{{ comment.message }}</p>
                <div>
                    <a href="" v-on:click.prevent="removeComment(index)" title="Excluir">Excluir</a>
                </div>
            </div>
        </div>
        <hr />
    </div>
</template>

<script>
import FormTodo from './FormTodo.vue'

export default {
    components: {
        FormTodo
    },
    data() {
        return {
            comments: []
        }
    },
    methods: {
        addComment(comment) {
            this.comments.push(comment);
        },

        removeComment(index) {
            this.comments.splice(index, 1)
        }
    },
    computed: {
        allComments() {
            return this.comments.map(comment => ({
                ...comment,
                name: comment.name.trim() === '' ? 'Anônimo' : comment.name
            }))
        }
    },
    watch: {
        comments(val) {
            console.log('val', val)
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>