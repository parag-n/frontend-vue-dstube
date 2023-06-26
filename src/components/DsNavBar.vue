<template>
  <div class="ds-navbar">
    <button @click="$emit('changeView', 'home')" class="ds-button red-button">
      DsTube
    </button>
    <input class="ds-searchbar" type="text" placeholder="Search" />
    <button
      @click="$emit('changeView', 'profile')"
      class="ds-button blue-button"
    >
      Profile
    </button>
  </div>
</template>

<script>
export default {
  name: "DsNavBar",
};
</script>

<style>
.ds-navbar {
  width: 100%;
  display: flex;
  justify-content: center;
}

.ds-searchbar {
  text-align: center;
  border-radius: 20px;
  width: 50%;
}
</style>
