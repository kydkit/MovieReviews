<template>
  <div id="addMovie" class="add-movie">
		<form @submit.prevent="" class="form-container">
		<div class="title">
			<label for="title">Title: </label>
			<input type="text" id="title" v-model="title">
		</div>
		<div class="slider-container">
			<label for="range">Rating: 1 </label>
			<input type="range" min="1" max="5" value="4" class="slider" id="range" v-model="sliderValue"> 5
		</div>
		<div class="genre">
			<label for="genre">Genre: </label>
			<select id="genre" v-model="genre">
			<option value="Drama">Drama</option>
			<option value="Comedy">Comedy</option>
			<option value="Sci-Fi">Sci-Fi</option>
			<option value="Documentary">Documentary</option>
			<option value="Kids">Kids</option>
			</select>
		</div>
		
		<div class="desc-container">
			<label for="description">Description: </label>
			<textarea id="desc" placeholder="Some text here..." v-model="add"></textarea>
			<div class="button-container">
			<button @click="reset" class="clear-button" id="clear-button">Clear</button>
			<button @click="addReview"  class="add-button" id="add-button">Add</button>
			</div>
		</div>
		</form>
		<div v-bind:style="{display: hasReview}"  class="noReviews">
			<p >No Reviews Yet</p>
		</div>
	</div>
</template>

<script>
export default {
  data() {
		return {
				title: "",
				sliderValue: 3,
				genre: "",
				add: "", 
				hasReview: "block"
		}
  }, 

  methods: {
		reset(){
			this.title = "",
			this.sliderValue = 3, 
			this.genre = "",
			this.add = ""
		},

    addReview(){
			let movies = {
				title: this.title,
				sliderValue: this.sliderValue,
				genre: this.genre,
				add: this.add
			}
			if (this.sliderValue > 0 && this.title.length > 0){
				this.$emit('add-review', movies),
				this.hasReview = "none", 
				this.title= "",
				this.sliderValue = 3,
				this.genre = "", 
				this.add = ""
			} else {
				return
			}
    }
  }

}
</script>

<style>
  .form-container {
	width: 300px;
	height: 350px;
	background-color: rgba(255, 255, 255, .5);
	border-radius: 10px;
	padding: 1.2rem;
	display: flex;
	flex-direction: column;
	justify-content: space-around;
	align-items: flex-start;
}

.noReviews {
	margin-top: 20px;
	width: 300px;
	height: 100px;
	background-color: rgba(255, 255, 255, .5);
	border-radius: 10px;
	padding: 1.2rem;
}

textarea {
	resize: none;
	width: 100%;
	height: 150px;
}

.button-container {
	display: flex;
	justify-content: space-between;
}
</style>