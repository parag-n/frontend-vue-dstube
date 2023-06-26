<template>
  <div class="homepage">
    <div
      v-for="card in cards"
      :key="card.id"
      v-show="!card.isHidden"
      class="card"
    >
      <img
        @click="$emit('showView', card)"
        :src="card.imgSrc"
        class="thumbnail"
      />
      <div class="description">
        <h2 id="title">{{ card.title }}</h2>
        <h5 id="views">{{ card.views }} Views</h5>
        <h4 id="creator">
          {{ card.creator.firstname }} {{ card.creator.lastname }}
        </h4>
        <p id="caption">{{ card.desc.substring(0, 100) }}...</p>
        <button @click="$emit('remove', card.id)" class="ds-button">
          Remove
        </button>
      </div>
    </div>
    <h6 class="results">Showing {{ results }} results</h6>
  </div>
</template>

<script>
export default {
  name: "HomePage",

  props: ["cards"],

  computed: {
    results: function () {
      let count = 0;
      this.cards.forEach((card) => {
        if (card.isHidden == false) count++;
      });
      return count;
    },
  },
};
</script>

<style>
.card {
  display: flex;
  justify-content: center;
  /* align-self: center; */
  padding: 8px;
}

.thumbnail {
  width: 22%;
  border-radius: 15px;
  aspect-ratio: 16/9;
  object-fit: cover;
  background-color: black;
}

.description {
  align-items: flex-start;
  text-align: left;
  width: 50%;
  /* margin-left: 15px; */
  padding: 15px;
}

#title {
  font-size: medium;
  margin-top: -10px;
}

#views {
  font-size: small;
  margin-top: -5px;
}

#creator {
  font-size: medium;
  margin-top: -10px;
}
</style>
