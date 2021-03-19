<template>
<div class="v-main-wrapper">
   <div class="w-main-wrapper">
      <div class="rectangle">
        <div class="question"><p>Задать вопрос</p></div>

      <form>
        <input 
        type="text" 
        placeholder="Фамилия Имя Отчество *"
        v-model="name">
       
       <input 
        type="text" 
        placeholder="Телефон *"
        v-model="phone">
        
        <input 
        type="text" 
        placeholder="Email"
        v-model="eMail">

        <button @click="sendData">ОТПРАВИТЬ ЗАПРОС</button>

        </form>



      </div>

    </div>

</div>
</template>




<script>
import axios from 'axios'




export default {
    name: 'v-main-wrapper',
    components: {
        
    },
  
    props: {},
    data() {
        return {
                name: '',
                phone: '',
                eMail: ''  
        }
    },
    computed: {
      
    },
     methods: {
         sendData() {
             axios.post('https://digital-spectr.com/ac/academy.php', {name: this.name, phone: this.phone, eMail: this.eMail})
             .then(response => {
                 console.log(response)
             })
         }       
     }
}

 
       
         
  

</script>




<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
.v-main-wrapper {
  width: 1024px;
  height: 768px;
  border: 1px solid green;
}
.rectangle {
  width: 481px;
  height: 392px;
  margin-top: 31px;
  margin-left: 272px;
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
  border: 1px solid khaki;
  font-family: roboto;
  font-weight: 700;
  font-style: normal;
  font-size: 24px;
  line-height: 20px;
  color: #3B3D43;
}
input{
 padding: 0;
  width: 401px;
  height: 48px;
border: none;
margin-top: 25px;
margin-left: 40px;
border-radius: 6px;
}
input[type=text] {
  width: 386px;
  padding-left: 15px;
 
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

</style>