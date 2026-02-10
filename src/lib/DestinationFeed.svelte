<script>
  import DestinationCard from './DestinationCard.svelte';
  
  const images = [
    "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRWjtvPGTt_ruBjlj1g_YJQZjK0AwRbgjEtmA&s",
    "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRMWR3Hljt98NSumEqDY69kc6_ceasBUxXdvA&s",
    "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSoYeOtnn5MIG7nJUYOsFK4BdRbp7I5JR_wsQ&s",
    "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ4TRqslwu3wM7Ozti2BdEFPllYGDuBJmp_rQ&s",
    "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS2cB9DXfGL1HAcgAZXH_PnMWslPWlqZb9W7g&s"
  ];

  const destinations = [
    { id: 1, title: "Angkor Wat Temple", location: "Siem Reap, Cambodia", image: images[0], price: "$120", rating: 4.9 },
    { id: 2, title: "Tropical Paradise", location: "Koh Rong, Cambodia", image: images[1], price: "$85", rating: 4.8 },
    { id: 3, title: "Mountain Escape", location: "Mondulkiri, Cambodia", image: images[2], price: "$250", rating: 4.7 },
    { id: 4, title: "Heritage Palace", location: "Phnom Penh, Cambodia", image: images[3], price: "$150", rating: 4.9 },
    { id: 5, title: "Beachside Luxury", location: "Sihanoukville, Cambodia", image: images[4], price: "$320", rating: 5.0 },
    { id: 6, title: "Ancient Jungle", location: "Preah Vihear, Cambodia", image: images[0], price: "$90", rating: 4.6 }
  ];

  function handleExplore(event) {
    dispatch('explore', event.detail);
  }

  function handleBook(event) {
    alert(`Thank you for your interest in ${event.detail.title}! Our agent will contact you soon.`);
  }

  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
</script>

<div class="destination-feed">
  <div class="section-header">
    <h2 class="section-title">Popular Destinations</h2>
    <p class="subtitle">Handpicked locations for your next adventure</p>
  </div>

  <div class="destination-grid">
    {#each destinations as dest (dest.id)}
      <DestinationCard {...dest} on:book={handleBook} on:explore={handleExplore} />
    {/each}
  </div>
</div>

<style>
  .destination-feed {
    padding: 20px 0;
  }
  .section-header {
    margin-bottom: 40px;
    text-align: center;
  }
  .subtitle {
    color: var(--text-muted);
    font-size: 1.1rem;
  }
</style>
