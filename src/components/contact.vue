<template>
  <div class="content">
    <div id="sidebar">
      <div class="mui--text-white mui--text-display1 mui--align-vertical">
        Вопросы
        <br>
        Пожелания
        <small class="author">by site author</small>
      </div>
    </div>
    <div id="content" class="mui-container-fluid">
      <div class="mui-row">
        <div class="mui-col-sm-10 mui-col-sm-offset-1">
          <br>
          <br>
          <div class="mui--text-black-54 mui--text-body2">Здесь вы можете написать письмо владельцу сайта</div>
          <div class="mui-divider"></div>
          <br>
          <form class="mui-form"
          id="form"
          @blur="checkForm"
          method="post"
          v-on:submit.prevent="funcSubmit"
          >
          <div class="mui-textfield mui-textfield--float-label">
            <input   required minlength="4" maxlength="40"
            id="name"
            v-model="name"
            type="text"
            name="name"
            @blur="isEmailValid"
            >
            <label for="question-input">Ваш Имя</label>
          </div>
          <div class="mui-textfield mui-textfield--float-label">
            <input  required minlength="4" maxlength="40"
            id="email"
            v-model="email"
            type="email"
            name="email"
            >
            <label for="question-input">Ваш email</label>
          </div>
          <div class="mui-textfield mui-textfield--float-label">
            <input   required minlength="10" maxlength="256"
            id="question-input"
            v-model="message"
            type="text"
            name="message"
            @blur="isEmailValid"
            >
            <label for="question-input">Ваше письмо</label>
          </div>

          <button type="submit"  id="submit" class="mui-btn mui-btn--primary" :disabled="islValid" >Отправить сообщение</button>
          <p v-if="errors.length">
            <b>Пожалуйста исправьте указанные ошибки:</b>
            <ul>
              <li v-for="error in errors">{{ error }}</li>
            </ul>
          </p>
        </form>
        <br>
        <br>
        <div class="mui--text-black-54 mui--text-body2">Ваш вопрос</div>
        <div class="mui-divider">{{message}}</div>
        <br>
        <div id="list"></div>
      </div>
    </div>
  </div>

</div>
</template>
<script>

export default{
  name:'contact',
  data() {
    return {
      errors: [],
      name: '',
      email: '',
      movie: '',
      message: '',
      islValid: true,
    }
  },
  methods:{
    checkForm(){
      this.errors = [];
      if (!this.name) {
        this.errors.push('Укажите имя.');
      }
      if (!this.email) {
        this.errors.push('Укажите электронную почту.');
      }
      if (!this.validEmail(this.email)) {
        this.errors.push('Укажите корректный адрес электронной почты.');
      }
      if(!this.message){
        this.errors.push('Напишите вопрос.');
      }
      else if (!this.errors.length) {

        return true;

      }
      e.preventDefault();
    },
    validEmail(email) {
      var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

      return re.test(email);
    },
    isEmailValid(){
      if(this.name.length>3  ){
        if(this.message.length>10){
          this.islValid = false
        }
      }
    },
    funcSubmit(event){

      const question ={
        name: this.name,
        message: this.message,
        mail: this.email,
        //    text: input.value.trim(), // создаем объект с вопросом и датой  (trim удаляет лишние пробелы)
        date: new Date().toJSON()
      }
      console.log(question)
      return  fetch('https://podcast-my.firebaseio.com/question.json',{
        method:'POST',
        body: JSON.stringify(question),
        headers:{
          'Content-Type':'application/json'
        }
      })
      .then(
        this.name = '',
        this.message = 'сообщение отправлено',
        this.email=""
      )
    }
  },

}


</script>
<style scoped>
html,
body {
  height: 100%;
}

html,
body,
input,
textarea,
button {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-shadow: 1px 1px 1px rgba(0, 0, 0, 0.004);
}
.mui--text-white{
  text-align: left;
}

/**
* Sidebar CSS
*/

#sidebar {
  background-color: #2196f3;
  padding: 15px;
  padding-top: 30px;
}
.mui--text-black-54{
  margin-top: 30px;
}
@media (min-width: 768px) {
  #sidebar {
    position: fixed;
    top: 0;
    bottom: 0;
    width: 200px;
    height: 100%;
    padding-top: 55px;
  }
}


/**
* Content CSS
*/
@media (min-width: 768px) {
  #content {
    margin-left: 180px;
  }
}
.author{
  font-size: 0.8rem;
}

</style>
