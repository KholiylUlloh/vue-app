<template>
  <div class="container">
    <h1>Users</h1>
    <div class="inputWrap">
      <input
        @input="name = $event.target.value"
        :value="name"
        type="text"
        placeholder="Enter Your Name"
      />
      <input
        @input="comment = $event.target.value"
        :value="comment"
        type="text"
        placeholder="Enter Your Comment"
      />
      <button @click="createComment">Add comment</button>
    </div>
    <div class="user" v-for="(comment, idx) in comments" :key="comment.id">
      <div>
        <div><b>Name:</b> {{ comment.name }}</div>
        <div><b>Comment:</b> {{ comment.comment }}</div>
      </div>
      <span @click="removeComment(idx)">X</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      comments: [
        {
          id: 1,
          name: "John",
          comment: "Lorem ipsum dolor sit amet, consectetur",
        },
        {
          id: 2,
          name: "Jane",
          comment: "Lorem ipsum dolor sit amet, consectetur",
        },
        {
          id: 3,
          name: "Tom",
          comment: "Lorem ipsum dolor sit amet, consectetur",
        },
      ],
      name: "",
      comment: "",
    };
  },
  methods: {
    createComment() {
      const newComment = {
        id: this.comments.length + 1,
        name: this.name,
        comment: this.comment,
      };
      this.comments.push(newComment);
    },
    removeComment(idx) {
      this.comments.splice(idx, 1);
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.user {
  border: 2px solid gray;
  margin-top: 10px;
  padding: 10px;
  width: 30%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.inputWrap {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 100%;
  margin-bottom: 20px;
}

input {
  width: 20%;
  margin: 0 auto;
  padding: 7px 10px;
  font-size: 16px;
}

button {
  width: 10%;
  margin: 0 auto;
  padding: 7px 10px;
}

span{
  cursor: pointer;
}
</style>
