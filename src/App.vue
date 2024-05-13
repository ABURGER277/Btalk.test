<template>
  <header>
    Copy messenger application
  </header>

  <!-- sidebar -->
  <div class="grid-container">
    <div class="grid-item">
      <div class="icon">
        <button @click="personmodalOn()"><img id="Person-Icon" src="./assets/img/icon-person.png" alt="Person Icon"></button>
        <button @click="messengermodalOn()"><img id="Messenger-Icon" src="./assets/img/icon-message.png" alt="Messenger Icon"></button>
      </div>
    </div>

    <div class="grid-item">
      <!-- 유저(친구) 조회 모달 -->
      <div v-if="personmodal == true">
        <div v-for="(user, index) in users" :key="index" class="user-list" @click="chatmodalOn(user)">
          <img :src="require(`@/assets/img/usericon${user.icon}.png`)" alt="usericon"  class="usericon">
          <h4 style="display:inline-block;">{{ user.user }}</h4>
        </div>
      </div>
      <!-- 내 채팅방 목록 모달 -->
      <div v-if="messengermodal == true">
        <div v-for="(chat, index) in chats" :key="index" class="chat-list" @click="chatmodalOn();">
          <h4 style="margin: 0">{{ chat.chatID }}</h4>
          <p style="margin: 5px">{{ chat.content }}</p>
        </div>
      </div>
    </div>

    <!-- 채팅창 -->
    <div class="grid-item">
      <!-- 기본 값 -->
      <div class="chat-default" v-if="chatmodal == false">
        <div class="chat-default-icon">
          <img src="./assets/img/icon-startchat.png">
          <br/><strong>start new chat</strong>
        </div>
      </div>
      <!-- 채팅 방 -->
      <div class="chat-room" v-if="chatmodal == true">
        <div v-for="(content, index) in contents" :key="index" :class="{ 'chat-room-content-send': index % 2 === 0, 'chat-room-content-receive': index % 2 !== 0 }" v-html="content">
           
        </div>
      </div>
      <div class="chat-write" v-if="chatmodal == true">
        <div class="chat-write-content" id="content" contenteditable="true" @keydown.enter.prevent="sendMessage()"></div>
        <div class="chat-write-sendbutton">
          <button style="border-color:#f0f0f0">
            <img id="sendbutton" src="./assets/img/icon-send.png" alt="sendbutton" @click="sendMessage()">
          </button>
        </div>
      </div>
    </div>
    <!-- 채팅창 끝 -->
  </div>

  <footer>
    example for Btalk
  </footer>
</template>

<script>
import users from './assets/data/userdata.js'

export default {
  name: 'App',
  components: {
    
  },
  data() {
    return {
      chatmodal: false,
      personmodal: false,
      messengermodal: true,
      users : users,
      // axios로 받아와서 chatID, chatContet로 구분하여 기입.
      chats: [
      { chatID: '채팅방 1', content: '채팅 내용 1' },
      { chatID: '채팅방 2', content: '채팅 내용 2' },
      { chatID: '채팅방 3', content: '채팅 내용 3' },
      // 다른 채팅방에 대한 정보를 추가할 수 있습니다.
      ],

      // chatID에 해당하는 채팅 내용.
      contents: [
        '채팅내용',
        '채팅내용',
        '채팅내용',
        '채팅내용<br/>채팅내용',
        '채팅내용',
        '채팅내용<br/>채팅내용',
        '채팅내용<br/>채팅내용<br/>채팅내용',
        '채팅내용<br/>채팅내용',
        '채팅내용',
        '채팅내용<br/>채팅내용<br/>채팅내용',
        '채팅내용',
        '채팅내용',
        '채팅내용',
        '채팅내용',
        '채팅내용',
        '채팅내용'
      ]
    }
    
  },
  mounted() {

  },
  methods: {
    personmodalOn() {
      this.personmodal = true;
      this.messengermodal = false;
    },
    messengermodalOn() {
      this.personmodal = false;
      this.messengermodal = true;
    },
    chatmodalOn() {
      this.chatmodal = true;
    },
    handleEnter(event) {
    // 엔터 키가 눌렸을 때 실행할 코드
      if (!event.shiftKey) { // 쉬프트 키와 함께 눌리지 않은 경우에만 실행
        this.sendMessage();
      }
    },
    sendMessage() {  
      let content = document.getElementById("content").innerHTML; 
      console.log(content);
      document.getElementById("content").innerHTML='';
    }
  }
}
</script>

<style>
body {
  margin: 0px;
  box-sizing: border-box;
  background-color: #4c84e0;
}
header {
  font-size: 40px;
  font-weight: bold;
  font-style: italic;
  color: white;
}
footer {
  padding:5px;
  height: 20px;
  font-style: italic;
  color: white;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}
.grid-container {
  display: grid;
  grid-template-columns: 100px 1fr 1fr; /* 3개의 열 생성 */
  gap: 5px; /* 열 사이의 간격 설정 */
}

.chat-default {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 90%; 
}

.grid-item {
  height: 550px;
  background-color: #f0f0f0;
  padding: 10px;
  border-radius: 5px;
  overflow-y: auto;
}

.user-list {
  margin: 5px;
  padding: 5px;
  background-color: #f0f0f0;
  border-radius: 10px;
  border: none;
  text-align: left;
}

.user-list:hover {
  background-color: lightgray;
  cursor: pointer;
}

.chat-list {
  margin: 5px;
  padding: 5px;
  background-color: #f0f0f0;
  border-radius: 10px;
  text-align: left;
}

.chat-list:hover {
  background-color: lightgray;
  cursor: pointer;
}

.chat-room {
  height: 80%;
  background-color: #f0f0f0;
  border-radius: 10px;
  overflow-y: auto;
}

.chat-room > div {
  margin: 15px;
  padding: 10px;
  border-radius: 10px;
}

.chat-room-content-send {
  background-color: rgba(255, 255, 0, 0.671);
  text-align: right;
}

.chat-room-content-receive {
  background-color: white;
  text-align: left;
}

.chat-write {
  display: flex;
  justify-content: space-between;
  align-items:center;
  margin: 5px, 5px, 5px, 5px;
  height:15%;
  background-color: white;
  border-radius: 10px;
}

.chat-write-content {
  margin:10px;
  padding:3px;
  flex-grow: 1;
  border: 0;
  height: 60px;
  text-align: left;
  overflow-y: auto;
}

.chat-write-sendbutton {
  margin:20px;
}

.chat-write-sendbutton:hover {
  background-color: lightgray;
  cursor: pointer;
}

.usericon {
  display: inline-block;
  width: 30px; height: auto;
}

.icon button {
  background-color: #f0f0f0;
  margin-bottom:10px;
  border-color: #f0f0f0;
}

button:hover {
  background-color: lightgray;
  cursor: pointer;
}

#Person-Icon{
  border: none;
  height:40px;
}

#Messenger-Icon{
  height:40px;
}

</style>
