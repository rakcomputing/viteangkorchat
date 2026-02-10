<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let contact = { name: 'Chat' };
  export let messages = [
    { id: 1, text: "Hey there!", sent: false },
    { id: 2, text: "Hi! How are you?", sent: true }
  ];

  let newMessage = '';

  function closeChat() {
    dispatch('close');
  }

  function sendMessage() {
    if (newMessage.trim()) {
      messages = [...messages, { id: Date.now(), text: newMessage, sent: true }];
      newMessage = '';
    }
  }
</script>

<div class="chat-box">
  <div class="chat-header" on:click={closeChat}>
    <div class="avatar">👤</div>
    <div class="chat-title">{contact.name}</div>
    <div class="header-actions">
      <span>📞</span>
      <span>📹</span>
      <span>−</span>
      <span class="close" on:click|stopPropagation={closeChat}>✕</span>
    </div>
  </div>

  <div class="message-area">
    {#each messages as msg}
      <div class="message" class:sent={msg.sent}>
        <div class="bubble">{msg.text}</div>
      </div>
    {/each}
  </div>

  <div class="chat-input-area">
    <div class="input-icons">➕ 📷 🃏 📎</div>
    <input type="text" placeholder="Aa" bind:value={newMessage} on:keydown={(e) => e.key === 'Enter' && sendMessage()} />
    <div class="send-icon" on:click={sendMessage}>👍</div>
  </div>
</div>

<style>
  .chat-box {
    position: fixed;
    bottom: 0;
    right: 80px;
    width: 330px;
    height: 455px;
    background: var(--fb-white);
    border-radius: 8px 8px 0 0;
    box-shadow: 0 12px 28px 0 rgba(0, 0, 0, 0.2), 0 2px 4px 0 rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    z-index: 2000;
  }
  .chat-header {
    background: var(--fb-white);
    padding: 8px;
    display: flex;
    align-items: center;
    border-bottom: 1px solid var(--fb-divider);
    border-radius: 8px 8px 0 0;
    cursor: pointer;
  }
  .chat-header:hover {
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }
  .avatar {
    width: 32px;
    height: 32px;
    background: var(--fb-light-gray);
    border-radius: 50%;
    margin-right: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .chat-title {
    font-weight: 600;
    flex: 1;
  }
  .header-actions {
    display: flex;
    gap: 12px;
    color: var(--fb-blue);
    cursor: pointer;
    font-size: 18px;
  }
  .close {
    font-weight: bold;
  }

  .message-area {
    flex: 1;
    overflow-y: auto;
    padding: 12px;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  .message {
    display: flex;
    width: 100%;
  }
  .message.sent {
    justify-content: flex-end;
  }
  .bubble {
    max-width: 80%;
    padding: 8px 12px;
    border-radius: 18px;
    font-size: 15px;
    line-height: 1.4;
  }
  .message:not(.sent) .bubble {
    background-color: var(--fb-bg);
  }
  .message.sent .bubble {
    background-color: var(--fb-blue);
    color: white;
  }

  .chat-input-area {
    padding: 8px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .input-icons {
    display: flex;
    gap: 8px;
    color: var(--fb-blue);
    font-size: 14px;
  }
  .chat-input-area input {
    flex: 1;
    background: var(--fb-bg);
    border: none;
    border-radius: 20px;
    padding: 8px 12px;
    outline: none;
  }
  .send-icon {
    font-size: 20px;
    cursor: pointer;
    color: var(--fb-blue);
  }
</style>
