# Site-insta <!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Chat com Atendimento</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="chat-container">
    <div class="chat-box" id="chat-box">
      <div class="bot-message">Olá! Bem-vindo ao nosso atendimento.</div>
      <div class="bot-message">Como posso te ajudar hoje?</div>
    </div>
    <input type="text" id="user-input" placeholder="Digite sua mensagem..." />
    <button onclick="sendMessage()">Enviar</button>
  </div>
  <script src="script.js"></script>
</body>
</html>

body {
  font-family: Arial, sans-serif;
  background-color: #f2f2f2;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.chat-container {
  width: 100%;
  max-width: 400px;
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  padding: 15px;
}

.chat-box {
  height: 300px;
  overflow-y: auto;
  margin-bottom: 10px;
  border: 1px solid #ddd;
  padding: 10px;
}

.bot-message, .user-message {
  margin-bottom: 10px;
  padding: 8px;
  border-radius: 5px;
}

.bot-message {
  background-color: #e1e1e1;
  align-self: flex-start;
}

.user-message {
  background-color: #d1e7dd;
  align-self: flex-end;
  text-align: right;
}

input[type="text"] {
  width: 70%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  width: 25%;
  padding: 10px;
  background-color: #0077b6;
  color: white;
  border: none;
  border-radius: 5px;
  margin-left: 5%;
}
function sendMessage() {
  const input = document.getElementById("user-input");
  const message = input.value.trim();
  if (message === "") return;

  const chatBox = document.getElementById("chat-box");

  const userMessage = document.createElement("div");
  userMessage.className = "user-message";
  userMessage.innerText = message;
  chatBox.appendChild(userMessage);

  input.value = "";

  setTimeout(() => {
    const botMessage = document.createElement("div");
    botMessage.className = "bot-message";
    
    if (message.toLowerCase().includes("instagram")) {
      botMessage.innerHTML = `Claro! Clique <a href="https://www.instagram.com/sua_pagina" target="_blank">aqui</a> para ir ao nosso Instagram.`;
    } else {
      botMessage.innerText = "Entendi! Se quiser ver mais, posso te levar ao nosso Instagram.";
    }

    chatBox.appendChild(botMessage);
    chatBox.scrollTop = chatBox.scrollHeight;
  }, 1000);
}
