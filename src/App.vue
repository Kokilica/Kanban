<template>
  <div id="app">
    <h1>KANBAN</h1>
    <Button />
    <main class="flexbox">
      <Board id="1">
        <b>
          <h1>TO DO</h1>
        </b>
        <Card id="one" draggable="true"></Card>
        <Card id="two" draggable="true"></Card>
      </Board>
      <Board id="2">
        <b>
          <h1>IN PROGRESS</h1>
        </b>
        <Card id="three" draggable="true"></Card>
        <Card id="four" draggable="true"></Card>
      </Board>
      <Board id="3">
        <b>
          <h1>DONE</h1>
        </b>
        <Card id="five" draggable="true"></Card>
      </Board>
    </main>
  </div>
</template>

<script>
import Board from "./components/Board";
import Card from "./components/Card";
import Button from "./components/Button";

export default {
  name: "app",
  components: {
    Board,
    Card,
    Button
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

* {
  margin: 5px;
  padding: 0;
}

.flexbox {
  display: flex;

  width: 100%;
  max-width: 1000px;
  height: 100vh;
  max-height: 700px;
  overflow: hidden;
  margin: 0 auto;
  padding: 5px;
}

.flexbox .board {
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 500px;
  background-color: darkgray;
  padding: 15px;
  border: 3px solid black;
}

.flexbox .board .card {
  display: flex;
  flex-direction: column;
  padding: 15px;
  background-color: #f3f3f3;
  width: 85%;
  height: 30%;
  cursor: pointer;
  margin-bottom: 15px;
}

$orange: #e96c40;
$green: #45d440;
$blue: #3c76e2;
$red: #e23c49;

#one {
  background: $green;
}

#two {
  background: $orange;
}

#three {
  background: $orange;
}

#four {
  background: $blue;
}

#five {
  background: $red;
}
</style>
