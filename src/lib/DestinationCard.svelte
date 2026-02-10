<script>
  export let image = "";
  export let title = "Destination Name";
  export let location = "Location, Country";
  export let price = "$0";
  export let rating = 5.0;

  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  function handleExplore() {
    dispatch('explore', { image, title, location, price, rating });
  }
</script>

<div class="dest-card fade-in">
  <div class="card-image" style="background-image: url({image})">
    <div class="badge">Trending</div>
    <div class="overlay">
      <button class="btn-explore" on:click={handleExplore}>Explore Now</button>
    </div>
  </div>
  <div class="card-content">
    <div class="header">
      <h3>{title}</h3>
      <div class="rating">⭐ {rating}</div>
    </div>
    <div class="location">📍 {location}</div>
    <div class="footer">
      <div class="price">From <span>{price}</span></div>
      <button class="btn-book" on:click={() => dispatch('book', { title })}>Book</button>
    </div>
  </div>
</div>

<style>
  .dest-card {
    background: var(--surface);
    border-radius: 24px;
    overflow: hidden;
    box-shadow: var(--shadow);
    transition: transform 0.3s ease;
  }

  .dest-card:hover {
    transform: translateY(-10px);
  }

  .card-image {
    height: 240px;
    background-size: cover;
    background-position: center;
    position: relative;
  }

  .badge {
    position: absolute;
    top: 20px;
    left: 20px;
    background: var(--glass);
    backdrop-filter: blur(5px);
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 12px;
    font-weight: 700;
    color: var(--primary-dark);
  }

  .overlay {
    position: absolute;
    inset: 0;
    background: rgba(0,0,0,0.3);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.3s;
  }

  .dest-card:hover .overlay {
    opacity: 1;
  }

  .btn-explore {
    background: white;
    color: var(--primary-dark);
    border: none;
    padding: 12px 24px;
    border-radius: 30px;
    font-weight: 700;
    cursor: pointer;
  }

  .card-content {
    padding: 24px;
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 8px;
  }

  h3 {
    font-size: 1.25rem;
    font-weight: 700;
  }

  .rating {
    font-weight: 700;
    color: var(--secondary);
  }

  .location {
    color: var(--text-muted);
    font-size: 14px;
    margin-bottom: 20px;
  }

  .footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px solid #eee;
    padding-top: 16px;
  }

  .price {
    font-size: 14px;
    color: var(--text-muted);
  }

  .price span {
    font-size: 1.25rem;
    font-weight: 800;
    color: var(--primary-dark);
    display: block;
  }

  .btn-book {
    background: var(--bg-color);
    border: 1.5px solid var(--primary);
    color: var(--primary);
    padding: 8px 20px;
    border-radius: 30px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.2s;
  }

  .btn-book:hover {
    background: var(--primary);
    color: white;
  }
</style>
