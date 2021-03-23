<template>
<div class="v-main-wrapper">
   <div class="w-main-wrapper">
      <div class="rectangle">
        <div class="question"><p>Задать вопрос</p></div>

      <form
      @submit="checkForm"
  action="https://digital-spectr.com/ac/academy.php"
  method="post"
  novalidate="true"
      >
    <input
      id="name"
      v-model="name"
      type="text"
      name="name"
       placeholder="Фамилия Имя Отчество *"
    >





       <div class="phoneInput">

       <input 
        type="phone" 
        id="phone"
        name="phone"
        placeholder="Телефон *"
        v-model="phone">
       </div>
        



        <input 
        type="email" 
        id="email"
        placeholder="Email"
        v-model="email"
        name="email"
        >
        

        <button>ОТПРАВИТЬ ЗАПРОС</button>
        </form>

    



      </div>
      <div class="errors">
    <p v-if="errors.length">
    <b>Пожалуйста, исправьте указанные ошибки:</b>
    <p 
    v-for="error in errors"
    :key="error.message"> {{error.message}}</p>
      </div>
  

    </div>

</div>
</template>




<script>





export default {
    name: 'v-main-wrapper',
    components: {
        
    },
  
    props: {},
    data() {
        return {  
               errors: [],
               
    name: null,
    email: null,
    phone: null

        }
    },
    computed: {
      
    },
     methods: {
           
    checkForm: function (e) {
      this.errors = [];

      if (!this.name) {
        this.errors.push({message:'Укажите имя.'});
      } else if (!this.validName(this.name)) {
        this.errors.push({message:'Укажите корректно ФИО.'});
      }


       if (!this.phone) {
        this.errors.push({message:'Укажите номер телефона.'});
      } else if (!this.validPhone(this.phone)) {
        this.errors.push({message:'Укажите корректно номер телефона.'});
      }


      if (!this.email) {
        this.errors.push({message:'Укажите электронную почту.'});
      } else if (!this.validEmail(this.email)) {
        this.errors.push({message:'Укажите корректный адрес электронной почты.'});
      }

      if (!this.errors.length) {
        return true;
      }

      e.preventDefault();
    },
    validEmail: function (email) {
      var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
  

    validName: function (name) {
      var re = /^[А-ЯЁ][а-яё]*([-][А-ЯЁ][а-яё]*)?\s[А-ЯЁ][а-яё]*\s[А-ЯЁ][а-яё]*$/;
      return re.test(name);
    },


     validPhone: function (phone) {
      var re = /^((8|\+7)[- ]?)?(\d{3}[- ]?)?[\d- ]{7,10}$/;
      return re.test(phone);
    },

  
     }
}

 
       
         
  

</script>




<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

.w-main-wrapper {
width: 1024px;
height: 768px;
padding-top: 31px;
margin: auto;
}
.rectangle {
  width: 481px;
  height: 392px;
 
  margin: auto;
  border-radius: 12px;
  background: #F7F5F9;
  filter: drop-shadow(5px 5px 15px rgba(0, 0, 0, 0.25));
  display: flex;
  flex-direction: column;
}

.question  p{
width: 168px;
margin-left: 40px;
margin-top: 40px;
margin-bottom: 0px;
  font-family: Roboto;
  font-weight: 700;
  font-style: normal;
  font-size: 24px;
  line-height: 20px;
  color: #3B3D43;
}
input{
font-family: Roboto;
 padding: 0;
  width: 401px;
  height: 48px;
border: none;
margin-top: 25px;
margin-left: 40px;
border-radius: 6px;
font-size: 15px;
line-height: 20px;
color: #D0C9D6;

}
input:hover {
 border: 1px solid #854FC8;
}
input:focus {
  outline-color: #854FC8;
}
button:hover  {
color: green ;
}
button:focus {
  color: palevioletred;
}


input[type=text] {
  padding-left: 14px;
}
input[type=phone] {
  padding-left: 14px;
}
input[type=email] {
  padding-left: 14px;
}
button {
width: 401px;
height: 48px;
margin-left: 40px;
margin-top: 25px;
border-radius: 6px;
box-shadow: 0px 7px 64px rgba(0, 0, 0, 0.07);
background: #6979F8;
color: #FFFFFF;
border: none;
font-family: Roboto;
font-weight: 400;
font-size: 17px;
line-height: 22px;
text-align: center;
}
.errors p{
color: red;
}
.errors {
margin: auto;
width: 400px;
padding-top: 20px
}
</style>