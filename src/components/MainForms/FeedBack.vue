<template>
  <div class="feedback-container">
    <h1 class="feedback-title">Обратная связь</h1>
    <form @submit.prevent="addComment">
      <textarea
        v-model="newCommentText"
        @input="checkMaxLength"
        placeholder="Напишите ваш комментарий"
        maxlength="120"
        rows="3"
        class="comment-input"
      ></textarea>
      <button type="submit" class="submit-button">Отправить</button>
      <hr />
    </form>

    <div class="comments">
      <div v-for="(comment, index) in comments" :key="index" class="comment">
        <p class="comment-text">{{ comment.text }}</p>
        <p class="comment-time">{{ comment.time }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FeedbackPage",
  data() {
    return {
      newCommentText: "",
      comments: [],
    };
  },
  methods: {
    addComment() {
      if (this.newCommentText.trim() === "") return;

      const currentTime = new Date().toLocaleTimeString();
      this.comments.push({
        text: this.newCommentText,
        time: currentTime,
      });
      this.newCommentText = "";
    },
    checkMaxLength(event) {
      if (event.target.value.length > 120) {
        event.target.value = event.target.value.slice(0, 120);
      }
    },
  },
};
</script>

<style>
.feedback-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.feedback-title {
  text-align: center;
  color: #fff;
  margin-bottom: 20px;
}

.comment-input {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  resize: vertical;
}

.submit-button {
  padding: 10px 20px;
  background-color: #a16e83;
  color: #333;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  float: right;
}
hr {
  margin-top: 50px;
}

.comments {
  margin-top: 20px;
}

.comment {
  background-color: #f8f8f8;
  padding: 10px;
  border-radius: 4px;
  margin-top: 5px;
  margin-bottom: 5px;
  overflow-y: auto;
}

.comment-text {
  word-wrap: break-word;
}

.comment-time {
  text-align: right;
  font-size: 0.8em;
  margin-top: 5px;
}
</style>
