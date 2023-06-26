<template>
  <div class="viewpage">
    <img :src="this.card.imgSrc" class="player" />
    <div>
      <h2>{{ this.card.title }}</h2>
      <h4>{{ this.card.views }} Views</h4>
      <h4
        v-show="this.likeCount > 5 && this.likeCount < 15"
        class="ds-badge green"
      >
        Popular
      </h4>
      <h4
        v-show="this.likeCount >= 15 && this.likeCount < 50"
        class="ds-badge red"
      >
        Trending
      </h4>
      <h3>
        {{ this.card.creator.firstname }} {{ this.card.creator.lastname }}
      </h3>
    </div>
    <div>
      <button class="ds-button" @click="increaseCount">
        Like {{ this.likeCount }}
      </button>
      <button class="ds-button" @click="decreaseCount">Dislike</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ViewPage",
  data() {
    return {
      likeCount: 3,
    };
  },
  props: ["card"],
  methods: {
    increaseCount() {
      this.likeCount++;
    },
    decreaseCount() {
      if (this.likeCount > 0) this.likeCount--;
    },
  },
};
</script>

<style>
.player {
  width: 80%;
  margin: 5px;
}
</style>
