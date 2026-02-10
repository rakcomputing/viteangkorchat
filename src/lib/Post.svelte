<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let author = "User Name";
  export let time = "Just now";
  export let content = "This is a post content.";
  export let likes = 0;
  export let comments = 0;
  export let shares = 0;

  let liked = false;

  function toggleLike() {
    liked = !liked;
    if (liked) likes++;
    else likes--;
  }
</script>

<div class="post">
  <div class="post-header">
    <div class="avatar">👤</div>
    <div class="header-info">
      <div class="author">{author}</div>
      <div class="time">{time}</div>
    </div>
    <div class="more">...</div>
  </div>

  <div class="post-content">
    {content}
  </div>

  <div class="post-stats">
    <div class="likes-count">👍 {likes}</div>
    <div class="other-stats">
      <span>{comments} comments</span>
      <span>{shares} shares</span>
    </div>
  </div>

  <div class="post-actions">
    <button class="action-btn" class:active={liked} on:click={toggleLike}>
      <span class="icon">👍</span> Like
    </button>
    <button class="action-btn">
      <span class="icon">💬</span> Comment
    </button>
    <button class="action-btn">
      <span class="icon">⤴️</span> Share
    </button>
  </div>
</div>

<style>
  .post {
    background: var(--fb-white);
    border-radius: 8px;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
    margin-bottom: 16px;
    padding: 12px 16px;
  }
  .post-header {
    display: flex;
    align-items: center;
    margin-bottom: 12px;
  }
  .avatar {
    width: 40px;
    height: 40px;
    background: var(--fb-light-gray);
    border-radius: 50%;
    margin-right: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
  }
  .author {
    font-weight: 600;
    font-size: 15px;
  }
  .time {
    color: var(--fb-gray);
    font-size: 13px;
  }
  .more {
    margin-left: auto;
    cursor: pointer;
    color: var(--fb-gray);
  }
  .post-content {
    font-size: 15px;
    line-height: 1.4;
    margin-bottom: 12px;
  }
  .post-stats {
    display: flex;
    justify-content: space-between;
    padding: 10px 0;
    border-bottom: 1px solid var(--fb-divider);
    color: var(--fb-gray);
    font-size: 14px;
  }
  .post-actions {
    display: flex;
    padding-top: 4px;
  }
  .action-btn {
    flex: 1;
    background: transparent;
    border: none;
    padding: 8px;
    border-radius: 4px;
    color: var(--fb-gray);
    font-weight: 600;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    transition: background 0.2s;
  }
  .action-btn:hover {
    background: var(--fb-hover);
  }
  .action-btn.active {
    color: var(--fb-blue);
  }
  .icon {
    font-size: 18px;
  }
</style>
