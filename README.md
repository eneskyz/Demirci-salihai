<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>demircisalih AI</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="chat-container">
        <header>
            <h1>🤖 demircisalih AI</h1>
            <p>Yapay zekâ asistanınız</p>
        </header>

        <div class="chat-box" id="chat-box"></div>

        <div class="input-area">
            <input type="text" id="user-input" placeholder="Bir şey yaz..." />
            <button id="send-btn">Gönder</button>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
body {
    background-color: #101820;
    color: #f2f2f2;
    font-family: 'Segoe UI', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.chat-container {
    width: 90%;
    max-width: 500px;
    background: #1e293b;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 0 15px rgba(0,0,0,0.4);
    display: flex;
    flex-direction: column;
}

header {
    text-align: center;
    background: #334155;
    padding: 15px;
}

header h1 {
    margin: 0;
    color: #38bdf8;
}

.chat-box {
    flex: 1;
    overflow-y: auto;
    padding: 15px;
    display: flex;
    flex-direction: column;
}

.message {
    margin: 10px 0;
    padding: 10px;
    border-radius: 8px;
    max-width: 80%;
    word-wrap: break-word;
}

.user {
    background-color: #38bdf8;
    color: #000;
    align-self: flex-end;
}

.bot {
    background-color: #475569;
    align-self: flex-start;
}

.input-area {
    display: flex;
    border-top: 1px solid #334155;
}

.input-area input {
    flex: 1;
    padding: 12px;
    border: none;
    background: #0f172a;
    color: white;
    font-size: 1rem;
    outline: none;
}

.input-area button {
    background: #38bdf8;
    border: none;
    padding: 12px 20px;
    cursor: pointer;
    font-weight: bold;
    color: #000;
    transition: background 0.2s;
}

.input-area button:hover {
    background: #0ea5e9;
}
const sendBtn = document.getElementById("send-btn");
const userInput = document.getElementById("user-input");
const chatBox = document.getElementById("chat-box");

sendBtn.addEventListener("click", sendMessage);
userInput.addEventListener("keypress", e => {
    if (e.key === "Enter") sendMessage();
});

function sendMessage() {
    const message = userInput.value.trim();
    if (message === "") return;
    appendMessage("user", message);
    userInput.value = "";

    // Simülasyon: Bot yanıtı
    setTimeout(() => {
        const reply = generateReply(message);
        appendMessage("bot", reply);
    }, 600);
}

function appendMessage(sender, text) {
    const msgDiv = document.createElement("div");
    msgDiv.classList.add("message", sender);
    msgDiv.textContent = text;
    chatBox.appendChild(msgDiv);
    chatBox.scrollTop = chatBox.scrollHeight;
}

function generateReply(input) {
    const responses = [
        "Merhaba! Ben demircisalih AI 🤖",
        "Nasıl yardımcı olabilirim?",
        "Harika bir soru sordun!",
        "Bunu daha önce hiç düşünmemiştim 🤔",
        "Evet, oldukça ilginç!"
    ];
    return responses[Math.floor(Math.random() * responses.length)];
}
