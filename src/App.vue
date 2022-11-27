

<template>
	<!-- App Wrapper -->
	<main class="app">
		<!-- Greeting -->
		<section class="greeting">
			<h2 class="title">
				What's up, <input type="text" id="name" placeholder="Name here" />
			</h2>
		</section>
		<!-- End of Greeting -->
		
		<!-- New Todo -->
		<section class="create-todo">
			<h3>CREATE A TODO</h3>
			<form id="new-todo-form">
				<h4>What's on your todo?</h4>
				<input 
					type="text" 
					placeholder="e.g. Get some milk"
					name="content"
					id="content" />
				
				<h4>Pick a category</h4>
				<div class="options">
					<label>
						<input type="radio" name="category" id="category1" value="business" /> 
						<span class="bubble business"></span>
						<div>Business</div>
					</label>
					<label>
						<input type="radio" name="category" id="category2" value="personal" />
						<span class="bubble personal"></span>
						<div>Personal</div>
					</label>
				</div>

				<input type="submit" value="Add todo" />
			</form>
		</section>
		<!-- End of New Todo -->

		<!-- Todo List -->
		<section class="todo-list">
  		<h3>TODO LIST </h3>
      <!-- ({{todoList.length}}) -->
			<div class="list" id="todo-list">
        <div v-for="todo in todoList" :class="`todo-item ${todo.done && 
          'done'}`">
          <label>
            <input type="checkbox" v-model="todo.done">
            <span :class="`bubble ${todo.category}`"></span>
          </label>
          <div class="todo-content">
            <input type="text" 
                   class="showTask" 
                   name="showTask" 
                   v-model="todo.content"/>
          </div>
          <!-- <div class="todo-date">
            <h3>
              <input type="text" class="showDate" name="showTask" v-model="todo.date">
            </h3>
          
          </div> -->
          <div class="actions">
            <button class="delete" @click="removeTodo(todo)">
              Delete
            </button>
          </div>
        </div>
      </div>

		</section>
		<!-- End of Todo List -->

	</main>
	<!-- End of App Wrapper -->


</template>
<!-- /* function choose date in calendar */
/* --------------Start------------- */ -->
<script >
  import Datepicker from 'vue3-datepicker';
import dateChooser from './components/dateChooser.vue';
export default {
  name: 'chooserApp',
  components: {
    dateChooser
  },
};
</script>
<!-- /* ---------------End------------- */
/* function choose date in calendar */ -->


<!-- <script>

</script> -->
