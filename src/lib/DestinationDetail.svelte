<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let destination = {
    title: "Destination Name",
    location: "Location",
    image: "",
    price: "$0",
    rating: 5.0
  };

  const description = `This is a breathtaking destination known for its stunning views and rich cultural history. Whether you're looking for adventure or relaxation, this location offers something for everyone. Experience the unique charm and natural beauty of ${destination.title}.`;

  function goBack() {
    dispatch('back');
  }

  function handleBook() {
    alert(`Booking initiated for ${destination.title}!`);
  }
</script>

<div class="detail-page fade-in">
  <button class="btn-back" on:click={goBack}>
    <span>←</span> Back to Explore
  </button>

  <div class="detail-container">
    <div class="detail-image" style="background-image: url({destination.image})">
      <div class="detail-overlay">
        <div class="detail-header-content">
          <div class="location-badge">📍 {destination.location}</div>
          <h1>{destination.title}</h1>
          <div class="meta-info">
            <span class="rating">⭐ {destination.rating} Rating</span>
            <span class="divider">|</span>
            <span class="reviews">1,200+ Reviews</span>
          </div>
        </div>
      </div>
    </div>

    <div class="detail-content">
      <div class="content-left">
        <h2>About this destination</h2>
        <p>{description}</p>
        <p>Enjoy luxury accommodations, guided tours, and authentic local cuisine. Our all-inclusive packages ensure you have a worry-free and memorable trip.</p>
        
        <div class="highlights">
          <div class="highlight-item">🏙️ 5-Star Hotel</div>
          <div class="highlight-item">🚗 Private Transport</div>
          <div class="highlight-item">🍷 Gourmet Dining</div>
          <div class="highlight-item">🎟️ Guided Tours</div>
        </div>
      </div>

      <div class="content-right">
        <div class="price-card glass-effect">
          <div class="price-header">Starts from</div>
          <div class="price-value">{destination.price}<span>/person</span></div>
          <p class="price-note">Includes taxes and fees</p>
          <button class="btn-book-large" on:click={handleBook}>Check Availability</button>
          <div class="trust-icons">
            <span>🛡️ Secure Booking</span>
            <span>💳 No Hidden Fees</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  .detail-page {
    padding: 20px 0;
    max-width: 1200px;
    margin: 0 auto;
  }

  .btn-back {
    background: none;
    border: none;
    color: var(--primary-dark);
    font-weight: 700;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 20px;
    font-size: 16px;
    transition: transform 0.2s;
  }

  .btn-back:hover {
    transform: translateX(-5px);
  }

  .detail-container {
    background: var(--surface);
    border-radius: 30px;
    overflow: hidden;
    box-shadow: var(--shadow);
  }

  .detail-image {
    height: 500px;
    background-size: cover;
    background-position: center;
    position: relative;
  }

  .detail-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to top, rgba(0,0,0,0.8), transparent);
    display: flex;
    align-items: flex-end;
    padding: 60px;
  }

  .detail-header-content {
    color: white;
  }

  .location-badge {
    background: var(--primary);
    padding: 4px 16px;
    border-radius: 20px;
    font-size: 14px;
    font-weight: 700;
    margin-bottom: 16px;
    display: inline-block;
  }

  h1 {
    font-size: 3.5rem;
    font-weight: 800;
    margin-bottom: 12px;
  }

  .meta-info {
    font-size: 1.1rem;
    display: flex;
    align-items: center;
    gap: 15px;
  }

  .rating {
    color: var(--secondary);
    font-weight: 700;
  }

  .detail-content {
    padding: 60px;
    display: grid;
    grid-template-columns: 1fr 380px;
    gap: 60px;
  }

  .content-left h2 {
    font-size: 2rem;
    margin-bottom: 24px;
  }

  .content-left p {
    font-size: 1.1rem;
    color: var(--text-muted);
    margin-bottom: 20px;
  }

  .highlights {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-top: 40px;
  }

  .highlight-item {
    background: var(--bg-color);
    padding: 16px;
    border-radius: 12px;
    font-weight: 600;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .price-card {
    padding: 40px;
    border-radius: 24px;
    border: 1px solid rgba(0,0,0,0.05);
    position: sticky;
    top: 100px;
  }

  .price-header {
    font-size: 14px;
    color: var(--text-muted);
    margin-bottom: 4px;
  }

  .price-value {
    font-size: 2.5rem;
    font-weight: 800;
    color: var(--primary-dark);
  }

  .price-value span {
    font-size: 1rem;
    color: var(--text-muted);
    font-weight: 500;
  }

  .price-note {
    font-size: 13px;
    color: var(--text-muted);
    margin: 10px 0 30px;
  }

  .btn-book-large {
    width: 100%;
    background: var(--primary);
    color: white;
    border: none;
    padding: 18px;
    border-radius: 15px;
    font-size: 1.1rem;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.2s;
    margin-bottom: 20px;
  }

  .btn-book-large:hover {
    background: var(--primary-dark);
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(0, 180, 216, 0.2);
  }

  .trust-icons {
    display: flex;
    flex-direction: column;
    gap: 10px;
    font-size: 14px;
    color: var(--text-muted);
  }

  @media (max-width: 992px) {
    .detail-content {
      grid-template-columns: 1fr;
    }
    .detail-overlay {
      padding: 30px;
    }
    h1 {
      font-size: 2.5rem;
    }
  }
</style>
