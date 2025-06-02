<template>
  <div id="sidebar">
    <div class="sidebar-container" :class="{ shrinked: isShrinked }">
      <div class="sidebar-header">
        <div class="header-icon-container">
          <div class="header-icon"><h4>RF</h4></div>
        </div>
        <h2 class="header-text shrink-text">Rajan Finance</h2>
        <div class="expansion" @click="isShrinked = !isShrinked">
          <ChevronsRight class="expansion-icon"></ChevronsRight>
        </div>
      </div>
      <div class="divider"></div>
      <ul class="nav-links-container">
        <li class="nav-link">
          <Home class="icon" />
          <p class="shrink-text">Home</p>
        </li>
        <li class="nav-link">
          <LayoutDashboard class="icon"></LayoutDashboard>
          <p class="shrink-text">Dashboard</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { Home, LayoutDashboard, ChevronsRight } from "lucide-vue-next";

const isShrinked = ref(false);
</script>

<style scoped>
.sidebar-container {
  color: #fff;
  min-height: 100vh;
  background: #000;
  max-width: 250px;
  transition: max-width 0.5s ease;
}
.sidebar-header {
  padding: 1rem;
  position: relative;
  display: flex;
  gap: 10px;
  align-items: center;
}
.divider {
  height: 2px;
  background: #fff;
  width: 100%;
  display: block;
}
.header-text {
  margin: 0;
  white-space: nowrap;
}
.header-icon {
  position: relative; /* Required for positioning ::after */
  border: 2px solid #fff;
  height: 1.5rem;
  width: 1.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1; /* Make sure content stays above ::after */
  transition: transform 0.5s;
  h4 {
    margin: 0;
  }
}
.header-icon::after {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  height: 100%;
  border: 2px solid #fff;
  transform: translate(-50%, -50%) scale(1.3); /* Center + scale */
  z-index: 0; /* Place behind content */
  transition: transform 0.5s;
}
.header-icon:hover {
  transform: rotate(-45deg);
  transition: transform 0.5s;
}
.header-icon:hover::after {
  transform: translate(-50%, -50%) rotate(90deg) scale(1.1);
  transition: transform 0.5s;
}
.nav-links-container {
  padding: 0;
  margin: 0;
  list-style-type: none;
  p {
    margin: 0;
    color: #ffffff96;
    transition: color 0.3s ease;
    white-space: nowrap;
  }
}
.nav-link {
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
  padding: 0.8rem 1rem;
  i {
    font-size: 1.3rem;
  }
}

.icon {
  stroke: #ffffff96;
  fill: none;
  transition: fill 0.3s ease, stroke 0.3s ease;
  width: 1.5rem; /* Ensure fixed size */
  height: 1.5rem; /* Ensure fixed size */
  flex-shrink: 0; /* Prevent shrinking */
}

.nav-link:hover .icon {
  stroke: #fff; /* Optional: match stroke */
}

.nav-link:hover p {
  color: #fff;
}

.nav-link:hover {
  background-color: #272727; /* Tailwind's gray-200 */
}

.expansion {
  position: absolute;
  right: -30px;
  background: #000;
  display: flex;
  justify-content: center;
  align-items: center;
  border-top-right-radius: 0.3rem;
  border-bottom-right-radius: 0.3rem;
  padding: 0.5rem;
}
.expansion-icon.active {
  transform: rotate(180deg);
  transition: transform 0.3s ease;
}

.expansion:hover .expansion-icon {
  transform: rotate(180deg);
}

.shrinked {
  max-width: 60px;
}

.shrinked .shrink-text {
  opacity: 0;
}
</style>
