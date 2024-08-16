<template>
  <div class="background">
    <div class="container-main">
      <main>
        <h1>Inspira Tech</h1>
        <h2>Encoraje uma garota tech 👩🏻‍💻</h2>
        <div class="container-message-form">
          <MessageForm @message-sent="addMessage" />
        </div>
      </main>
    </div>
    <div class="container-message-list">
      <main class="background-mural-avisos">
        <h3>💗 Mural de Avisos</h3>
        <MessageList :messages="messages" />
      </main>
    </div>
  </div>
</template>

<script>
import MessageForm from '../components/MessageForm.vue';
import MessageList from '../components/MessageList.vue';

export default {
  name: 'Home',
  components: {
    MessageForm,
    MessageList
  },
  data() {
    return {
      messages: JSON.parse(sessionStorage.getItem('messages')) || []
    };
  },
  watch: {
    messages(newMessages) {
      sessionStorage.setItem('messages', JSON.stringify(newMessages));
    }
  },
  methods: {
    addMessage(message) {
      if (message.trim()) {
        const uniqueMessages = Array.from(new Set([...this.messages, message]));
        this.messages = uniqueMessages;
      }
    }
  }
};
</script>

<style scoped>
.background {
  background-color: #FFC0CB; /* Cor de fundo rosa claro */
  padding: 20px; /* Adiciona algum espaçamento interno */
  min-height: 100vh; /* Garante que o fundo ocupe toda a altura da tela */
  display: flex; /* Ativa o modo flexbox */
  flex-direction: column; /* Alinha os itens verticalmente */
  align-items: center; /* Centraliza horizontalmente */
}

.background-mural-avisos {
  background-color: #ffffff;
  border: 1px solid #FF1493;
  border-radius: 10px;
}

.container-main {
  width: 50%;
  background-color: #ffffff;
  border: 1px solid #FF1493;
  border-radius: 20px;
  padding: 20px; /* Adiciona algum espaçamento interno ao container */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Adiciona uma sombra suave ao container */
}

h1 {
  font-family: "Englebert", cursive;
  color: #FF1493;
  text-align: center;
}

h2 {
  font-family: "Englebert", cursive;
  color: #000000;
  text-align: center;
}

.container-message-form {
  text-align: center;
  margin-bottom: 20px; /* Espaçamento abaixo do formulário */
}

.container-message-list {
  width: 50%;
  margin-top: 20px; /* Espaçamento acima da lista de mensagens */
}

h3 {
  font-family: "Englebert", cursive;
  color: #FF1493;
  text-align: center;
}
</style>