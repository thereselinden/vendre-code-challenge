<script setup></script>

<template>
  <header>
    <nav>
      <ul>
        <router-link :to="{ name: 'Home' }">Home</router-link>
        <router-link :to="{ name: 'Contact' }">Contact</router-link>
      </ul>
    </nav>
  </header>
  <main>
    <router-view />
  </main>
</template>

<style scoped></style>
