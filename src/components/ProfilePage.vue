<template>
  <div class="ds-profile">
    <input type="text" name="first_name" v-model="first_name" />
    <input type="text" name="last_name" :value="userDetails.last_name" />
    <input type="text" name="email" :value="userDetails.email" />
    <input type="text" name="mobile" :value="userDetails.mobile" />
    <div class="user-details">
      <p>First Name: {{ first_name }}</p>
      <p>Last Name: {{ userDetails.last_name }}</p>
      <p>Email: {{ userDetails.email }}</p>
      <p>Mobile: {{ userDetails.mobile }}</p>
    </div>
  </div>
</template>

<script>
export default{
    name:"ProfilePage",
    data(){
        return({
            first_name: this.userDetails.first_name
        })
    },
    props:["userDetails"]
}
</script>
