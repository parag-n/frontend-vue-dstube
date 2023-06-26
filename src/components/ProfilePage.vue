<template>
  <div class="ds-profile">
    <input type="text" name="first_name" v-model="first_name" />
    <input type="text" name="last_name" v-model="last_name" />
    <input type="text" name="email" v-model="email" />
    <input type="text" name="mobile" v-model="mobile" />
    <div class="user-details">
      <p>First Name: {{ first_name }}</p>
      <p>Last Name: {{ last_name }}</p>
      <p>Email: {{ email }}</p>
      <p>Mobile: {{ mobile }}</p>
    </div>
  </div>
</template>

<script>
export default{
    name:"ProfilePage",
    data(){
        return({
            first_name: this.userDetails.first_name,
            last_name: this.userDetails.last_name,
            email: this.userDetails.email,
            mobile: this.userDetails.mobile
        })
    },
    props:["userDetails"]
}
</script>
