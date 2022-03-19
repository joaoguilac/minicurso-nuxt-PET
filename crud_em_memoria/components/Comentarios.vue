<template>
  <div class="container">
    <h1>Formulario</h1>
    <form @submit.prevent="addComment()">
      <input required placeholder="Usuário" type="text" name="user" class="form-control" v-model="name"/>
      <br>
      <textarea required placeholder="Digite seu comentário" name="message" class="form-control" v-model="message"></textarea>
      <br>
      <input type="submit" value="Comentar" class="btn btn-primary">
    </form>
    <hr>

    <h2>Comentários</h2>
    <br>
    <div id="messages" class="list-group">
      <p v-if="comments.length<=0">Sem comentários...</p>
      <div class="list-group-item" v-for="(comment, index) in comments" :key="index">
        <span>Usuário: <strong>{{ comment.name }}</strong></span>
        <p>{{ comment.message }}</p>
        <div>
          <a href="" title="Excluir" @click.prevent="removeComment(index)">Excluir</a>
          <a href="" title="Editar" @click.prevent="editComment(index)">Editar</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      comments: [],
      name: '',
      message: '',
      isEditing: false,
      index: 0
    }
  },

  methods: {
    addComment() {
      if (!this.isEditing) {
        this.comments.push({
          name: this.name,
          message: this.message,
        });

        this.name = '';
        this.message = '';
      }
      else {
        this.comments[this.index] = {
          name: this.name,
          message: this.message,
        };

        this.name = '';
        this.message = '';
        this.isEditing = false;
        this.index = 0;
      }
    },

    removeComment(index) {
      this.comments.splice(index, 1);
    },

    editComment(index) {
      let comment = this.comments[index];
      this.name = comment.name;
      this.message = comment.message;

      this.isEditing = true;
      this.index = index;

      alert('Editando comentário ' + (this.index + 1));
    }
  }
}
</script>

<style>

</style>
