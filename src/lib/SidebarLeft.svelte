<script>
  const menuItems = [
    { name: 'John Doe', icon: '👤' },
    { name: 'Friends', icon: '👥' },
    { name: 'Groups', icon: '👨‍👩‍👧‍👦' },
    { name: 'Marketplace', icon: '🏪' },
    { name: 'Watch', icon: '📺' },
    { name: 'Memories', icon: '⏰' },
    { name: 'Saved', icon: '🔖' }
  ];
</script>

<aside class="sidebar-left">
  {#each menuItems as item}
    <div class="menu-item">
      <span class="icon">{item.icon}</span>
      <span class="label">{item.name}</span>
    </div>
  {/each}
  <div class="divider"></div>
  <h3>Your Shortcuts</h3>
  <div class="menu-item">
    <span class="icon">🎮</span>
    <span class="label">Gaming Group</span>
  </div>
</aside>

<style>
  .sidebar-left {
    padding: 16px 8px;
  }
  .menu-item {
    display: flex;
    align-items: center;
    padding: 8px;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.2s;
  }
  .menu-item:hover {
    background: var(--fb-hover);
  }
  .icon {
    font-size: 24px;
    width: 36px;
    height: 36px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-right: 12px;
  }
  .label {
    font-weight: 500;
  }
  .divider {
    height: 1px;
    background: var(--fb-divider);
    margin: 8px 0;
  }
  h3 {
    padding: 8px;
    color: var(--fb-gray);
    font-size: 17px;
    font-weight: 600;
  }
</style>
