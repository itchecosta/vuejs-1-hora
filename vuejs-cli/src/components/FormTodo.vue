<template>
    <div class="form-todo form-group">
          <p>
              <input placeholder="nome" type="text" class="form-control" name="author" v-model="name">
          </p>
          <p>
              <textarea placeholder="Comentário" name="message" id="message" class="form-control" v-model="message"></textarea>
          </p>
          <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
      </div>
</template>

<script>

export default {
    data() {
      return {
          comments: [],
          name: '',
          message: ''
      }
  },
  methods: {
      addComment() {
          if (this.message.trim() === '') {
              return;
          }

          this.$emit('add-todo', {
             name: this.name,
             message: this.message
          })

          this.name = '';
          this.message = '';
      }
  }
}
</script>