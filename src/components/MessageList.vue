<template>
  <div class="message-list">
    <div v-for="(message, index) in messages" :key="index" class="message">
      {{ message }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'MessageList',
  props: {
    messages: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.message-list {
  padding: 10px;
}

.message {
  background-color: #ffffff;
  border: 3px solid #FF1493;
  border-radius: 15px;
  padding: 10px;
  margin: 10px 0;
  position: relative;
}
</style>