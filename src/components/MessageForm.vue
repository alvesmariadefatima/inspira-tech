<template>
  <div class="message-form">
    <input
      v-model="newMessage"
      placeholder="Digite aqui uma mensagem de inspiração..."
    />
    <div>
      <button @click="submitMessage">Enviar</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newMessage: '',
      messages: [] // Armazena as mensagens
    };
  },
  methods: {
    submitMessage() {
      if (this.newMessage.trim()) {
        this.messages.push(this.newMessage);
        this.saveMessages(); // Salva as mensagens no sessionStorage
        this.newMessage = ''; // Limpa o campo após enviar
      }
    },
    saveMessages() {
      sessionStorage.setItem('messages', JSON.stringify(this.messages));
    },
    loadMessages() {
      const storedMessages = sessionStorage.getItem('messages');
      if (storedMessages) {
        this.messages = JSON.parse(storedMessages);
      }
    }
  },
  created() {
    this.loadMessages(); // Carrega as mensagens quando o componente é criado
  }
};
</script>

<style scoped>
.message-form {
  text-align: center;
  width: 80%; /* Define a largura do formulário */
  margin: 0 auto; /* Centraliza o formulário horizontalmente */
}

input {
  margin-bottom: 10px; /* Espaçamento abaixo do campo de input */
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 80%; /* Garante que o input use toda a largura disponível */
  box-sizing: border-box; /* Inclui o padding e a borda no cálculo da largura */
}

button {
  font-family: "Englebert", cursive;
  background-color: #FF1493;
  border-radius: 5px; /* Reduzido para um visual mais compacto */
  color: #ffffff;
  border: none;
  padding: 6px 12px; /* Reduzido para diminuir o tamanho do botão */
  cursor: pointer; /* Adiciona um cursor de ponteiro ao passar sobre o botão */
  font-size: 14px; /* Reduzido para o tamanho do texto do botão */
  align-self: flex-start; /* Alinha o botão ao início do contêiner (opcional) */
}

button:hover {
  background-color: #ff69b4; /* Cor de fundo do botão ao passar o mouse */
}

.messages {
  margin-top: 20px; /* Espaçamento acima da lista de mensagens */
}
</style>