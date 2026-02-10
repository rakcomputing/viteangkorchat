<script>
  let searchQuery = '';
</script>

<nav class="navbar">
  <div class="nav-left">
    <div class="logo">
      <span class="logo-icon">🏯</span>
      <span class="logo-text">AngkorTravel</span>
    </div>
  </div>

  <div class="nav-middle">
    <a href="/" class="nav-link active">Explore</a>
    <a href="/destinations" class="nav-link">Destinations</a>
    <a href="/tours" class="nav-link">Tours</a>
    <a href="/deals" class="nav-link">Deals</a>
  </div>

  <div class="nav-right">
    <div class="search-bar">
      <span>🔍</span>
      <input type="text" placeholder="Where to?" bind:value={searchQuery} />
    </div>
    <button class="btn-primary">Book Now</button>
  </div>
</nav>

<style>
  .navbar {
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 40px;
    max-width: 1400px;
    margin: 0 auto;
  }

  .nav-left .logo {
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 24px;
    font-weight: 800;
    color: var(--primary-dark);
    cursor: pointer;
  }

  .logo-icon {
    font-size: 32px;
  }

  .nav-middle {
    display: flex;
    gap: 30px;
  }

  .nav-link {
    text-decoration: none;
    color: var(--text-main);
    font-weight: 600;
    font-size: 16px;
    transition: color 0.3s;
    position: relative;
  }

  .nav-link:hover {
    color: var(--primary);
  }

  .nav-link.active::after {
    content: '';
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 100%;
    height: 2px;
    background: var(--primary);
  }

  .nav-right {
    display: flex;
    align-items: center;
    gap: 20px;
  }

  .search-bar {
    display: flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,0,0,0.05);
    padding: 8px 16px;
    border-radius: 30px;
  }

  .search-bar input {
    border: none;
    background: transparent;
    outline: none;
    width: 120px;
    font-size: 14px;
  }

  .btn-primary {
    background: var(--primary);
    color: white;
    border: none;
    padding: 10px 24px;
    border-radius: 30px;
    font-weight: 700;
    cursor: pointer;
    transition: transform 0.2s, background 0.2s;
  }

  .btn-primary:hover {
    background: var(--primary-dark);
    transform: translateY(-2px);
  }
</style>
