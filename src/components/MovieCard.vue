<template>
<div id="movieCard" class="card-container">
    <div class="card-title">
      <span>Title: {{ review.title }}</span>
      <span>{{ review.sliderValue }}/5</span>
    </div>
    <div class="card-genre">
      <span>{{ review.genre }}</span>
    </div>
    <div class="card-desc">
      <span>Description: {{ review.add }}</span>
    </div>
</div>

</template>

<script>
export default {
  props: ['review'], 
}
</script>

<style>
.card-container {
  margin-top: 50px;
	width: 300px;
	height: auto;
	background-color: rgba(255, 255, 255, .5);
	border-radius: 10px;
	padding: 1.2rem;
}

.card-title {
  display: flex;
  justify-content: space-between;
  padding-bottom: 10px;
  font-size: 1.1rem;
}
.card-genre {
  text-align: right;
  padding-bottom: 20px;
  font-size: 1.1rem;
}

</style>