<template>
  <div class="container">
    <h1>Formulario</h1>
    <form @submit.prevent="addPost()">
      <input required placeholder="Título" type="text" name="title" class="form-control" v-model="title"/>
      <br>
      <input required placeholder="Id do usuário" type="text" name="id_user" class="form-control" v-model="userId"/>
      <br>
      <textarea required placeholder="Digite o comentário" name="message" class="form-control" v-model="message"></textarea>
      <br>
      <input type="submit" value="Postar" class="btn btn-primary">
    </form>
    <hr>

    <h2>Posts</h2>
    <br>
    <div id="messages" class="list-group">
      <p v-if="posts.length<=0">Sem posts...</p>
      <div class="list-group-item" v-for="(post, index) in posts" :key="index">
        <span>Título: <strong>{{ post.title }}</strong></span>
        <p>{{ post.body }}</p>
        <div>
          <a href="" title="Excluir" @click.prevent="removePost(index)">Excluir</a>
          <a href="" title="Editar" @click.prevent="editPost(index)">Editar</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [],
      title: '',
      userId: '',
      message: '',
      isEditing: false,
      index: 0
    }
  },

  async fetch() {
    const config = {
      params: {
        _limit: 5
      }
    };
    let response = await this.$axios.get('', config);
    this.posts = response.data;
  },

  methods: {
    async addPost() {
      if (!this.isEditing) {
        const newPost = {
          title: this.title,
          body: this.message,
          userId: this.userId
        };

        let response = await this.$axios.post('', newPost);
        this.posts.push(response.data);

        console.log('Resposta da requisição post:');
        console.log(response);
        console.log('Dados da requisição post:');
        console.log(response.data);

        this.title = '';
        this.userId = '';
        this.message = '';
      }
      else {
        let response = await axios.put(`${this.posts[this.index].id}`, data);
        console.log(response);

        this.posts[this.index] = {
          title: this.title,
          body: this.message,
          userId: this.userId
        };

        this.title = '';
        this.userId = '';
        this.message = '';
        this.isEditing = false;
        this.index = 0;
      }
    },

    async removePost(index) {
      const config = {
        params: {
          _limit: 5
        }
      };

      let response = await this.$axios.get('', config);
      console.log(response);
      response = await this.$axios.delete(`${this.posts[this.index].id}`);
      console.log('Resposta da requisição delete:');
      console.log(response);
      response = await this.$axios.get('', config);
      console.log(response);

      this.posts.splice(index, 1);
    },

    editPost(index) {
      let post = this.posts[index];
      this.title = post.title;
      this.userId = post.userId;
      this.message = post.message;

      this.isEditing = true;
      this.index = index;

      alert('Editando comentário ' + (this.index + 1));
    }
  }
}
</script>

<style>

</style>
