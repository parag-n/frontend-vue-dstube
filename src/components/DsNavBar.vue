<template>
    <div class="ds-navbar">
        <button @click="$emit('changeView', 'home')" class="ds-button" >DsTube</button>
        <input class="ds-searchbar" type="text">
        <button @click="$emit('changeView', 'profile')" class="ds-button" >Profile</button>
    </div>
</template>

<script>
    export default{
        name:"DsNavBar"
    }
</script>