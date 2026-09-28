<script setup>
// Import Vue helpers:
// ref() is used for reactive values that can change.
// computed() is used for values calculated from other reactive data.
import { ref, computed } from "vue";

//                                   Sorting

// Stores the field currently used for sorting.
// Default value is "subject".
const sortBy = ref("subject");

// Stores the sorting direction.
// Default value is ascending.
const sortOrder = ref("ascending");

//                                Categories Data

// Stores the category information shown on the homepage.
// This data is static for now, so it does not need to use ref().
const categories = [
  {
    // Category name
    name: "Creative Arts",

    // Icon shown on the category card(I used my Laptop Keyboard icons)
    icon: "🎨",

    // Short description
    description: "Drawing, painting & crafts",
  },

  {
    name: "Computing & Tech",
    icon: "💻",
    description: "Coding, robotics & games",
  },

  {
    name: "Sports & Fitness",
    icon: "⚽",
    description: "Football, tennis & fitness",
  },

  {
    name: "Music",
    icon: "🎵",
    description: "Piano, guitar & singing",
  },

  {
    name: "Science",
    icon: "🔬",
    description: "Experiments & discovery",
  },

  {
    name: "Academic Support",
    icon: "📚",
    description: "Maths, English & study skills",
  },
];

//                                Lesson Data

// Stores the classes and activities.
// ref() is used because lesson data can change later,
// for example when the number of available spaces decreases.
const lessons = ref([
  {
    // Unique ID for this lesson
    id: 1,

    // Lesson title
    subject: "Coding for Kids",

    // Defines whether this item is a Class or an Activity
    type: "Class",

    // Lesson location
    location: "Edgware",

    // Teacher name
    teacher: "Mr Wilson",

    // Lesson price
    price: 15,

    // Number of available spaces
    spaces: 8,

    // Lesson image
    image: "https://images.unsplash.com/photo-1516321318423-f06f85e504b3",
  },

  {
    id: 2,
    subject: "Football Club",
    type: "Activity",
    location: "Mill Hill",
    teacher: "Coach Taylor",
    price: 12,
    spaces: 5,
    image: "https://images.unsplash.com/photo-1579952363873-27f3bade9f55",
  },

  {
    id: 3,
    subject: "Art & Creativity",
    type: "Class",
    location: "Hendon",
    teacher: "Ms Carter",
    price: 14,
    spaces: 6,
    image: "https://images.unsplash.com/photo-1513364776144-60967b0f800f",
  },

  {
    id: 4,
    subject: "Piano Lessons",
    type: "Class",
    location: "Barnet",
    teacher: "Mrs Lee",
    price: 18,
    spaces: 4,
    image: "https://images.unsplash.com/photo-1520523839897-bd0b52f945a0",
  },

  {
    id: 5,
    subject: "Junior Basketball",
    type: "Activity",
    location: "Finchley",
    teacher: "Mr Davis",
    price: 13,
    spaces: 7,
    image: "https://images.unsplash.com/photo-1546519638-68e109498ffc",
  },

  {
    id: 6,
    subject: "Young Scientists",
    type: "Class",
    location: "Colindale",
    teacher: "Dr Smith",
    price: 16,
    spaces: 3,
    image: "https://images.unsplash.com/photo-1532094349884-543bc11b234d",
  },

  {
    id: 7,
    subject: "Chess Club",
    type: "Activity",
    location: "Edgware",
    teacher: "Mr Clark",
    price: 10,
    spaces: 5,
    image: "https://images.unsplash.com/photo-1586165368502-1bad197a6461",
  },

  {
    id: 8,
    subject: "English Workshop",
    type: "Class",
    location: "Hendon",
    teacher: "Ms Adams",
    price: 13,
    spaces: 9,
    image: "https://images.unsplash.com/photo-1509062522246-3755977927d7",
  },

  {
    id: 9,
    subject: "Kids Dance",
    type: "Activity",
    location: "Mill Hill",
    teacher: "Ms Harris",
    price: 12,
    spaces: 4,
    image: "https://images.unsplash.com/photo-1508700115892-45ecd05ae2ad",
  },

  {
    id: 10,
    subject: "Maths Club",
    type: "Class",
    location: "Finchley",
    teacher: "Mr Brown",
    price: 11,
    spaces: 6,
    image: "https://images.unsplash.com/photo-1509228468518-180dd4864904",
  },
]);

//                              Sorted Lesson

// computed() creates a derived value.
// Whenever sortBy or sortOrder changes,
// Vue automatically recalculates sortedLessons.
const sortedLessons = computed(() => {
  // Create a copy of the lessons array.
  // This prevents the original lessons array from being reordered directly.
  const result = [...lessons.value];

  // Sort the copied array.
  result.sort((a, b) => {
    // Read the selected property dynamically.
    // Example:
    // if sortBy = "subject", this becomes a.subject and b.subject.
    let first = a[sortBy.value];
    let second = b[sortBy.value];

    // Convert text values to lowercase
    // so sorting is not affected by uppercase/lowercase letters.
    if (typeof first === "string") {
      first = first.toLowerCase();
      second = second.toLowerCase();
    }

    // If the first value should come before the second value...
    if (first < second) {
      // Return -1 for ascending order
      // or 1 for descending order.
      return sortOrder.value === "ascending" ? -1 : 1;
    }

    // If the first value should come after the second value...
    if (first > second) {
      // Return 1 for ascending order
      // or -1 for descending order.
      return sortOrder.value === "ascending" ? 1 : -1;
    }

    // If both values are equal, keep their order unchanged.
    return 0;
  });

  // Return the sorted array.
  return result;
});
</script>

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

      <!-- Categories -->
      <section class="categories-section">
        <div class="section-title">
          <p>EXPLORE</p>
          <h2>Something for every interest</h2>
          <span>
            Discover after-school activities designed to inspire, challenge and
            entertain.
          </span>
        </div>

        <div class="categories-grid">
          <article
            v-for="category in categories"
            :key="category.name"
            class="category-card"
          >
            <div class="category-icon">
              {{ category.icon }}
            </div>

            <h3>{{ category.name }}</h3>

            <p>
              {{ category.description }}
            </p>
          </article>
        </div>
      </section>

      <!-- Classes & Activities -->
      <section class="lessons-section">
        <div class="lessons-header">
          <div>
            <p class="small-heading">DISCOVER</p>

            <h2>Popular Classes & Activities</h2>

            <p class="lesson-count">
              {{ sortedLessons.length }} experiences available
            </p>
          </div>

          <!-- Sorting -->
          <div class="sorting">
            <label>
              Sort by

              <select v-model="sortBy">
                <option value="subject">Subject</option>

                <option value="location">Location</option>

                <option value="price">Price</option>

                <option value="spaces">Spaces</option>
              </select>
            </label>

            <label>
              Order

              <select v-model="sortOrder">
                <option value="ascending">Ascending</option>

                <option value="descending">Descending</option>
              </select>
            </label>
          </div>
        </div>

        <!-- Lesson Cards -->
        <div class="lesson-grid">
          <article
            v-for="lesson in sortedLessons"
            :key="lesson.id"
            class="lesson-card"
          >
            <div class="lesson-image">
              <img :src="lesson.image" :alt="lesson.subject" />

              <span class="lesson-type" :class="lesson.type.toLowerCase()">
                {{ lesson.type }}
              </span>
            </div>

            <div class="lesson-content">
              <div class="lesson-title">
                <h3>
                  {{ lesson.subject }}
                </h3>

                <strong> £{{ lesson.price }} </strong>
              </div>

              <p class="lesson-info">📍 {{ lesson.location }}</p>

              <p class="lesson-info">👤 {{ lesson.teacher }}</p>

              <div class="lesson-bottom">
                <span class="spaces"> {{ lesson.spaces }} spaces left </span>

                <button>🛒 Add to Cart</button>
              </div>
            </div>
          </article>
        </div>
      </section>
    </main>
  </div>
</template>
