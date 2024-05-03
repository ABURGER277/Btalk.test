<template>
  <header>
    KaonI messenger application
  </header>

  <div class="grid-container">
    <div class="grid-item">
      side menu
    </div>

    <div class="grid-item">
      <div class="chat-list">
        <h4 style="margin : 0px">채팅방 1</h4>
        <p style="margin : 5px">채팅 내용</p>
      </div>
      <div class="chat-list">
        <h4 style="margin : 0px">채팅방 1</h4>
        <p style="margin : 5px">채팅 내용</p>
      </div>
      <div class="chat-list">
        <h4 style="margin : 0px">채팅방 1</h4>
        <p style="margin : 5px">채팅 내용</p>
      </div>
      <div class="chat-list">
        <h4 style="margin : 0px">채팅방 1</h4>
        <p style="margin : 5px">채팅 내용</p>
      </div><div class="chat-list">
        <h4 style="margin : 0px">채팅방 1</h4>
        <p style="margin : 5px">채팅 내용</p>
      </div>
      <div class="chat-list">
        <h4 style="margin : 0px">채팅방 1</h4>
        <p style="margin : 5px">채팅 내용</p>
      </div><div class="chat-list">
        <h4 style="margin : 0px">채팅방 1</h4>
        <p style="margin : 5px">채팅 내용</p>
      </div>
      <div class="chat-list">
        <h4 style="margin : 0px">채팅방 1</h4>
        <p style="margin : 5px">채팅 내용</p>
      </div>
    </div>

    <div class="grid-item">
      <div>
      </div>
    </div>
  </div>

  <footer>
    example for btalk
  </footer>
</template>

<script>


export default {
  name: 'App',
  components: {
    
  }
}
</script>

<style>
body {
  margin: 0px;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.grid-container {
  display: grid;
  grid-template-columns: 100px 1fr 1fr; /* 3개의 열 생성 */
  gap: 5px; /* 열 사이의 간격 설정 */
}

.grid-item {
  height: 500px;
  background-color: #f0f0f0;
  padding: 20px;
  border-radius: 5px;
}

.chat-list {
  margin: 0px;
  padding: 0px;
}
</style>
