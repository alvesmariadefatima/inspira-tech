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
  border: 1px solid #FF1493;
  border-radius: 15px;
  padding: 10px;
  margin: 10px 0;
  position: relative;
}

.message::before {
  content: '';
  position: absolute;
  bottom: -15px; /* Ajuste para posicionar a ponta do balão */
  left: 20px; /* Ajuste para posicionar a ponta do balão */
  width: 0;
  height: 0;
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-top: 15px solid #ffffff; /* Cor da ponta do balão */
}
</style>