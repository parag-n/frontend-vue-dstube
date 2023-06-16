<template>
  <div class="homepage">
    <div
      v-for="card in cards"
      :key="card.id"
      v-show="!card.isHidden"
      class="card"
    >
      <img :src="card.imgSrc" class="thumbnail"/>
      <div  class="description">
        <h2>{{ card.title }}</h2>
        <h5>{{ card.views }} Views</h5>
        <h4>{{ card.creator.firstname }} {{ card.creator.lastname }}</h4>
        <p>{{ card.desc }}</p>
        <button @click="$emit('remove', card.id)" class="ds-button">Remove</button>
      </div>
    </div>
    <h6 class="results">About {{ results }} results</h6>
  </div>
</template>

<script>
export default {
  name: "HomePage",

  props: ["cards"],

  computed:{
    results: function(){
      let count = 0;
      this.cards.forEach((card)=>{
        if(card.isHidden == false) count++;
      })
      return count;
    }
  }
};
</script>
