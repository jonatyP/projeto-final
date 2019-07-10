<template>
    <div id="scta" class="table-secondary">
        <div id="cadastroLivro" class="form-gruup ">
            <h2 align="center">{{ cabecalho }}</h2>
            <input v-model="novoLivro" @keyup.enter="addLivro" type="text" placeholder="Titulo do livro..." class="form-control">
            <br>
            <input v-model="novoAutor" @keyup.enter="addLivro" type="text" placeholder="Autor do livro..." class="form-control">
            <br/>
            <span class="input-group-btn">
                <button @click="addLivro" type="button" class="btn btn-success btn-block">Adicionar</button>
            </span>
            <br>
        </div>
        <div id="tblLivro">
            <hr>
            <ul>
                <li  class="toggle" v-for="livro of livros" :key="livro" v-bind:class="{ 'removido': livro.checked }">
                    <div class="checkbox">
                        <label>
                            <input type="checkbox" name="list" v-model="livro.checked">
                            <big>{{ livro.titulo }}</big> - <small>{{ livro.autor }}</small>
                            <span aligin="right" >
                                <button class="btn btn-outline-danger" @click="removeLivro(livro)"> x </button>
                            </span>                            
                        </label>
                    </div>
                </li>
            </ul>
        </div>
        <!--<footer class="footer" v-show="todos.length" v-cloak>
            <span class="todo-count">
                <strong>{{ remaining }}</strong> {{ remaining | pluralize }} left
            </span>
            <ul class="filters">
                <li><a href="#/all" :class="{ selected: visibility == 'all' }">Todos</a></li>
                <li><a href="#/active" :class="{ selected: visibility == 'active' }">Ativados</a></li>
                <li><a href="#/completed" :class="{ selected: visibility == 'completed' }">Concluído</a></li>
            </ul>
            <button class="clear-completed" @click="removeCompleted" v-show="livros.length > remaining">
                Clear completed
            </button>   
        </footer> -->
    </div>
</template>

<script>
export default {
    name: 'scta',
    data () {
        return {
            cabecalho: 'Livros Preferidos',
            livros: [],
            novoLivro: "",
            novoAutor: "",
            //visibility: 'all',
                                    
        }
    },
    mounted() {
        if (localStorage.getItem('livros')) {
            try {
                this.livros = JSON.parse(localStorage.getItem('livros'));
            } catch(e) {
                localStorage.removeItem('livros');
            }
        }
    },
    
    methods: {
        addLivro() {
            var titulo, autor,
            titulo = this.novoLivro.trim()
            autor = this.novoAutor.trim()
            if (!titulo && autor === "") {
                return
            }
            this.livros.push({titulo: titulo, autor: autor, checked: false })
            this.novoLivro = ""
            this.novoAutor = ""
            this.saveLivro();
        }, 
        removeLivro(livro){
            this.livros.splice(this.livros.indexOf(livro), 1)
            this.saveLivro();
        },
        saveLivro() {
            const parsed = JSON.stringify(this.livros);
            localStorage.setItem('livros', parsed);
        }        
    },
}
</script>
<style>

</style>
