<template>
  <v-app>
    <!-- Transparent Top App Bar with no shadow -->
    <v-app-bar app flat color="transparent" style="box-shadow: none;">
      <!-- Logo Section -->
      <v-img src="/logo/sasa-logo.png" height="100px" style="max-width: 100px;" contain></v-img>

      <!-- Spacer to push navigation links to the right -->
      <v-spacer></v-spacer>

      <!-- Navigation Links with customizable text color -->
      <v-btn text to="/" class="custom-text-color">Home</v-btn>
      <v-btn text to="/services" class="custom-text-color">Services</v-btn>
      <v-btn text to="/about-us" class="custom-text-color">About Us</v-btn>

      <!-- Dropdown for "Our Client" with an arrow indicator -->
      <v-menu v-model="clientMenu" offset-y open-on-hover>
        <template v-slot:activator="{ on, attrs }">
          <v-btn text v-bind="attrs" v-on="on" class="custom-text-color">
            Our Client
            <v-icon :class="{'rotate-arrow': clientMenu}" small>mdi-chevron-down</v-icon>
          </v-btn>
        </template>
        <v-list class="text-only-dropdown">
          <v-list-item to="/our-client">
            <v-list-item-title class="dropdown-text">Our Client</v-list-item-title>
          </v-list-item>
          <v-list-item to="/associate-company">
            <v-list-item-title class="dropdown-text">Associate Company</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <!-- Contact Us Link -->
      <v-btn text to="/contact-us" class="custom-text-color">Contact Us</v-btn>
    </v-app-bar>

    <!-- Main Content with Full Background -->
    <v-main class="main-background">
      <v-container fluid class="main-container">
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'default-layout',
  data() {
    return {
      clientMenu: false, // Controls the dropdown menu visibility
    };
  },
};
</script>

<style scoped>
/* Custom text color for links */
.custom-text-color {
  color: #4eb135;
  font-weight: 500;
  font-size: 0.9rem;
}

.custom-text-color:hover {
  color: #000000;
}

/* Dropdown arrow rotation */
.rotate-arrow {
  transform: rotate(180deg);
  transition: transform 0.3s ease;
}

/* Text-only dropdown items */
.text-only-dropdown {
  background-color: transparent !important; /* Ensure no background */
  box-shadow: none !important; /* Remove any shadow */
  padding: 0;
}

.v-list-item {
  padding: 0 !important;
}

.dropdown-text {
  color: #000000;
  font-size: 0.9rem;
  padding: 5px 15px;
}

.dropdown-text:hover {
  color: #4eb135; /* Change color on hover */
}

/* Full-width, full-height background for each page */
.main-background {
  background-color: #fffffffa;
  min-height: 50px;
  width: 100%;
  padding: 50;
  margin: 0;
  position: relative;
}

.main-container {
  max-width: 100% !important;
  padding: 0;
  margin: 0;
}
</style>
