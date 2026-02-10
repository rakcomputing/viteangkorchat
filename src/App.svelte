<script>
  import Navbar from './lib/Navbar.svelte';
  import DestinationFeed from './lib/DestinationFeed.svelte';
  import DestinationDetail from './lib/DestinationDetail.svelte';
  import ChatBox from './lib/ChatBox.svelte';

  let view = 'home'; // 'home' or 'detail'
  let selectedDestination = null;
  let showAssistant = false;
  const assistantContact = { name: "Travel Assistant 🏝️" };
  
  const heroImage = "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRWjtvPGTt_ruBjlj1g_YJQZjK0AwRbgjEtmA&s";

  function toggleAssistant() {
    showAssistant = !showAssistant;
  }

  function handleExplore(event) {
    selectedDestination = event.detail;
    view = 'detail';
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  function goBack() {
    view = 'home';
    selectedDestination = null;
  }
</script>

<div class="layout-container">
  <header>
    <Navbar />
  </header>

  {#if view === 'home'}
    <section class="hero" style="background-image: url({heroImage})">
      <div class="hero-overlay"></div>
      <div class="hero-content fade-in">
        <h1>Discover Your Next Adventure</h1>
        <p>Luxury travel experiences tailored just for you</p>
      </div>
    </section>

    <main class="main-content">
      <DestinationFeed on:explore={handleExplore} />
    </main>
  {:else if view === 'detail'}
    <main class="main-content">
      <DestinationDetail destination={selectedDestination} on:back={goBack} />
    </main>
  {/if}

  <button class="assistant-trigger" on:click={toggleAssistant}>
    <span class="icon">💬</span>
  </button>

  {#if showAssistant}
    <ChatBox contact={assistantContact} on:close={toggleAssistant} />
  {/if}
</div>

<style>
  .hero-content p {
    font-size: 1.5rem;
    font-weight: 500;
    opacity: 0.9;
  }

  .assistant-trigger {
    position: fixed;
    bottom: 30px;
    right: 30px;
    width: 60px;
    height: 60px;
    background: var(--primary);
    color: white;
    border: none;
    border-radius: 50%;
    font-size: 24px;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1500;
    transition: transform 0.2s;
  }

  .assistant-trigger:hover {
    transform: scale(1.1);
    background: var(--primary-dark);
  }
</style>
