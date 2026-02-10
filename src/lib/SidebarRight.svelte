<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  const contacts = [
    { id: 1, name: 'Anna Smith', online: true },
    { id: 2, name: 'David Lee', online: true },
    { id: 3, name: 'Sarah Wilson', online: false },
    { id: 4, name: 'James Brown', online: true },
    { id: 5, name: 'Emily Davis', online: false }
  ];

  function openChat(contact) {
    dispatch('openChat', contact);
  }
</script>

<aside class="sidebar-right">
  <div class="sidebar-header">
    <h3>Contacts</h3>
    <div class="header-icons">
      <span>🎥</span>
      <span>🔍</span>
      <span>...</span>
    </div>
  </div>
  
  {#each contacts as contact}
    <div class="contact-item" on:click={() => openChat(contact)}>
      <div class="avatar-container">
        <div class="avatar">👤</div>
        {#if contact.online}
          <div class="online-status"></div>
        {/if}
      </div>
      <span class="contact-name">{contact.name}</span>
    </div>
  {/each}
</aside>

<style>
  .sidebar-right {
    padding: 16px 8px;
  }
  .sidebar-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 8px;
    color: var(--fb-gray);
  }
  .header-icons {
    display: flex;
    gap: 12px;
    cursor: pointer;
  }
  .contact-item {
    display: flex;
    align-items: center;
    padding: 8px;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.2s;
  }
  .contact-item:hover {
    background: var(--fb-hover);
  }
  .avatar-container {
    position: relative;
    margin-right: 12px;
  }
  .avatar {
    width: 36px;
    height: 36px;
    background: var(--fb-light-gray);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
  }
  .online-status {
    position: absolute;
    bottom: 2px;
    right: 2px;
    width: 10px;
    height: 10px;
    background: #31a24c;
    border: 2px solid var(--fb-white);
    border-radius: 50%;
  }
  .contact-name {
    font-weight: 500;
  }
</style>
