<template>
  <div>
    <transition name="modal">
      <div v-if="isOpen">
        <div class="overlay" @click.self="isOpen = false;">
          <div class="modal">
            <h1>New Task</h1>
            <div class="form-group">
              <div class="container">
                <form>
                  <div class="row">
                    <div class="col-2">
                      <label class="col-25">Title</label>
                    </div>
                    <div class="col-75">
                      <input v-model="userData.title" type="text" placeholder="Enter title" required/>     
                    </div>
                  </div>
                  <div class="row">
                    <div class="col-25">
                      <label>Task</label>
                    </div>
                    <div class="col-75">
                      <textarea v-model="userData.text" placeholder="Write your task" style="height:200px" required></textarea>
                    </div>
                  </div>
                  <div class="row">
                    <button type="button" v-on:click="addTask">Add Task</button>
                    <button type="button" v-on:click="saveTask">Save Task</button>
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </transition>
    <button @click="isOpen = !isOpen;">{{ isOpen ? "Close" : "New Task" }}</button>
  </div>
</template>

<script>
export default {

  data: function() {
    return {
      isOpen: false,
      userData: {
            id: 0,
            type: "",
            title: "",
            text: "",
            sample: []
      }
    };
  },
  methods: {
   addTask: function(){
     this.sample.push({ id: this.id, type: this.type, title: this.title, text: this.text });
   },
   saveTask: function(){
     const data = JSON.stringify(this.sample);
     window.localStorage.setItem('sample', data);
   }
  }
};
</script>

<style scoped>
.modal {
  width: 500px;
  margin: 0px auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px 3px;
  transition: all 0.2s ease-in;
  font-family: Helvetica, Arial, sans-serif;
}

button {
  background-color: green;
  color: white;
  font-size: 1.1rem;
  width: 15%;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background: #00000094;
  z-index: 999;
  transition: opacity 0.2s ease;
}

* {
  box-sizing: border-box;
}

input[type="text"],
select,
textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  resize: vertical;
}

.container {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}

.col-25 {
  float: left;
  width: 25%;
  margin-top: 6px;
}

.col-75 {
  float: left;
  width: 75%;
  margin-top: 6px;
}

.row:after {
  content: "";
  display: table;
  clear: both;
}
</style>