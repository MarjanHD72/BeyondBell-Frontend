<template>
  <div>
    <!-- Navbar -->
    <header class="navbar">
      <div class="logo">
        <span class="logo-icon"
          ><img src="../public/Images/bell-logo.png" alt="Logo"
        /></span>
        <span>BeyondBell</span>
      </div>

      <nav class="nav-links">
        <a href="#">Home</a>
        <a href="#">Classes</a>
        <a href="#">Activities</a>
        <a href="#">Teachers</a>
        <a href="#">About</a>
      </nav>

      <div class="nav-actions">
        <button class="cart-button">
          🛒
          <span class="cart-count">0</span>
        </button>

        <button class="sign-in-button">Sign In</button>

        <button class="register-button">Register</button>
      </div>
    </header>

    <!-- Hero -->
    <main>
      <section class="hero">
        <div class="hero-content">
          <p class="hero-label">AFTER SCHOOL CLASSES & ACTIVITIES</p>

          <h1>
            Ignite
            <span class="yellow-text">Curiosity</span>
            <span class="blue-text">Beyond School.</span>
          </h1>

          <p class="hero-description">
            Engaging classes and activities to help every child explore their
            interests, build skills and make new friends.
          </p>

          <!-- Search -->
          <div class="search-box">
            <input
              type="text"
              placeholder="Search for classes, activities or locations..."
            />

            <button>Search</button>
          </div>

          <!-- Filters -->
          <div class="hero-filters">
            <button class="filter active">▦ All</button>

            <button class="filter">🎓 Classes</button>

            <button class="filter">🏃 Activities</button>
          </div>
        </div>

        <!-- Hero visual -->
        <div class="hero-visual">
          <div class="shape shape-one"></div>
          <div class="shape shape-two"></div>

          <img
            class="hero-kids-image"
            src="/Images/hero-kids.png"
            alt="Happy children holding school books"
          />

          <p class="hero-note">
            More than<br />
            just learning
          </p>
        </div>
      </section>
    </main>
  </div>
</template>
