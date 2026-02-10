<script>
  import Post from './Post.svelte';
  
  let newPostContent = '';
  let posts = [
    { id: 1, author: "Anna Smith", time: "2 hours ago", content: "Had a great day at the beach! 🏖️", likes: 12, comments: 2, shares: 1 },
    { id: 2, author: "David Lee", time: "5 hours ago", content: "Starting a new project with Svelte. Feeling excited! 🚀", likes: 25, comments: 8, shares: 3 },
    { id: 3, author: "Sarah Wilson", time: "Yesterday", content: "Does anyone have recommendations for a good coffee shop in the city?", likes: 5, comments: 15, shares: 0 }
  ];

  function handleCreatePost() {
    if (newPostContent.trim()) {
      const newPost = {
        id: posts.length + 1,
        author: "Me",
        time: "Just now",
        content: newPostContent,
        likes: 0,
        comments: 0,
        shares: 0
      };
      posts = [newPost, ...posts];
      newPostContent = '';
    }
  }
</script>

<div class="timeline">
  <div class="create-post">
    <div class="top">
      <div class="avatar">👤</div>
      <input type="text" placeholder="What's on your mind, Me?" bind:value={newPostContent} on:keydown={(e) => e.key === 'Enter' && handleCreatePost()} />
    </div>
    <div class="divider"></div>
    <div class="bottom">
      <div class="post-option"><span>🎥</span> Live Video</div>
      <div class="post-option"><span>📷</span> Photo/video</div>
      <div class="post-option"><span>😊</span> Feeling/activity</div>
    </div>
  </div>

  {#each posts as post (post.id)}
    <Post {...post} />
  {/each}
</div>

<style>
  .timeline {
    width: 100%;
  }
  .create-post {
    background: var(--fb-white);
    border-radius: 8px;
    padding: 12px 16px;
    margin-bottom: 16px;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
  }
  .top {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 12px;
  }
  .avatar {
    width: 40px;
    height: 40px;
    background: var(--fb-light-gray);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
  }
  .create-post input {
    background: var(--fb-bg);
    border: none;
    border-radius: 20px;
    padding: 10px 16px;
    flex: 1;
    cursor: pointer;
    font-size: 16px;
    outline: none;
  }
  .create-post input:hover {
    background: var(--fb-divider);
  }
  .divider {
    height: 1px;
    background: var(--fb-divider);
    margin-bottom: 8px;
  }
  .bottom {
    display: flex;
    justify-content: space-around;
  }
  .post-option {
    padding: 8px;
    display: flex;
    align-items: center;
    gap: 8px;
    cursor: pointer;
    border-radius: 8px;
    transition: background 0.2s;
    color: var(--fb-gray);
    font-weight: 600;
  }
  .post-option:hover {
    background: var(--fb-hover);
  }
  .post-option span {
    font-size: 22px;
  }
</style>
