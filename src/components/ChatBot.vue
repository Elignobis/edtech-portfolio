<template>
  <div class="chatbot-bar reveal">
    <p class="chatbot-desc">💬 Ask my AI assistant about my projects and experience</p>
    <div class="chat-input-row">
      <input
        v-model="userInput"
        type="text"
        placeholder="Ask about Sibongile's experience, projects..."
        class="chat-input"
        @keyup.enter="sendMessage"
        :disabled="loading"
      />
      <button class="send-btn" @click="sendMessage" :disabled="loading || !userInput.trim()">
        <i class="fa-solid fa-paper-plane"></i>
      </button>
    </div>

    <!-- Response popup -->
    <div v-if="reply" class="chat-reply">
      <div class="reply-bubble">
        <span class="bot-icon">🤖</span>
        <p>{{ reply }}</p>
      </div>
      <button class="clear-btn" @click="reply = ''">✕ Clear</button>
    </div>

    <div v-if="loading" class="chat-reply">
      <div class="reply-bubble">
        <span class="bot-icon">🤖</span>
        <div class="typing">
          <span></span><span></span><span></span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const userInput = ref('')
const reply = ref('')
const loading = ref(false)

const systemPrompt = `You are an AI assistant for Sibongile Rwayi's EdTech portfolio website. 
Answer questions ONLY about Sibongile and her work. Be friendly, professional and concise.

NAME: Sibongile Rwayi
ROLE: Programme Manager | Education & Social Impact | Youth Development | EdTech

SKILLS: UI/UX Design, Vue.js, Curriculum Design, EdTech Tools, Analytics, Collaboration

PROJECTS:
1. Interactive Math Quiz App - gamified quiz for Grade 4-6 learners
2. Teacher Dashboard - analytics for tracking student progress
3. Online Learning Portal - full LMS with course management

CONTACT: GitHub: https://github.com/elignobis

Keep answers to 2-3 sentences max. If asked anything unrelated, politely redirect.`

async function sendMessage() {
  if (!userInput.value.trim() || loading.value) return

  const question = userInput.value.trim()
  userInput.value = ''
  loading.value = true
  reply.value = ''

  try {
    const response = await fetch('https://api.anthropic.com/v1/messages', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        model: 'claude-sonnet-4-20250514',
        max_tokens: 1000,
        system: systemPrompt,
        messages: [{ role: 'user', content: question }]
      })
    })

    const data = await response.json()
    reply.value = data.content?.[0]?.text || "Sorry, I couldn't get a response!"
  } catch {
    reply.value = "Something went wrong. Please try again!"
  } finally {
    loading.value = false
  }
}
</script>
<style scoped>
.chatbot-bar {
  max-width: 650px;
  margin: 0 auto;
  padding: 2rem 2rem 3rem;
}

.chatbot-desc {
  text-align: center;
  color: var(--text-muted);
  font-size: 0.9rem;
  margin-bottom: 0.75rem;
}

.chat-input-row {
  display: flex;
  gap: 0.75rem;
}

.chat-input {
  flex: 1;
  padding: 0.85rem 1.2rem;
  border-radius: 12px;
  border: 1.5px solid var(--border);
  background: var(--surface);
  color: var(--text);
  font-size: 0.92rem;
  font-family: 'Outfit', sans-serif;
  outline: none;
  transition: border 0.2s;
}

.chat-input:focus { border-color: var(--primary); }
.chat-input::placeholder { color: var(--text-muted); }

.send-btn {
  width: 48px;
  height: 48px;
  border-radius: 12px;
  background: linear-gradient(135deg, #1e40af, #3b82f6);
  color: white;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s;
  flex-shrink: 0;
}

.send-btn:hover { transform: translateY(-2px); box-shadow: 0 4px 15px rgba(37,99,235,0.4); }
.send-btn:disabled { opacity: 0.5; cursor: not-allowed; transform: none; }

/* Reply */
.chat-reply {
  margin-top: 1rem;
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 1rem;
}

.reply-bubble {
  display: flex;
  align-items: flex-start;
  gap: 0.6rem;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 0.75rem 1rem;
  flex: 1;
  font-size: 0.9rem;
  color: var(--text);
  line-height: 1.6;
}

.bot-icon { font-size: 1.1rem; flex-shrink: 0; }

.clear-btn {
  background: none;
  border: 1px solid var(--border);
  color: var(--text-muted);
  border-radius: 8px;
  padding: 0.4rem 0.75rem;
  font-size: 0.8rem;
  cursor: pointer;
  white-space: nowrap;
  font-family: 'Outfit', sans-serif;
  transition: all 0.2s;
  flex-shrink: 0;
}

.clear-btn:hover { color: var(--text); border-color: var(--text); }

/* Typing */
.typing {
  display: flex;
  align-items: center;
  gap: 4px;
  padding: 4px 0;
}

.typing span {
  width: 7px;
  height: 7px;
  background: var(--text-muted);
  border-radius: 50%;
  animation: bounce 1.2s infinite;
}

.typing span:nth-child(2) { animation-delay: 0.2s; }
.typing span:nth-child(3) { animation-delay: 0.4s; }

@keyframes bounce {
  0%, 60%, 100% { transform: translateY(0); }
  30% { transform: translateY(-6px); }
}

@media (max-width: 640px) {
  .chatbot-bar { padding: 1.5rem 1.5rem 2rem; }
}
</style>