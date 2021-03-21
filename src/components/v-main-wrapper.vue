<template>
<div class="v-main-wrapper">
   <div class="w-main-wrapper">
      <div class="rectangle">
        <div class="question"><p>Задать вопрос</p></div>

      
        <input 
        type="text" 
        required
        placeholder="Фамилия Имя Отчество *"
        v-model="ame">
        


       <div class="phoneInput">
       
       <input 
        type="text" 
        required
        placeholder="Телефон *"
        v-model="phone">
       </div>
        



        <input 
        type="text" 
        required
        placeholder="Email"
        v-model="email">

        <button type ="submit" @click="sendData">ОТПРАВИТЬ ЗАПРОС</button>

        



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
                focused: false,
                name: '',
                phone: '',
                email: ''  
        }
    },
    computed: {
      
    },
     methods: {
         sendData() {
           axios.defaults.headers.common['Authorization'] = 5611057;
             axios.post('https://digital-spectr.com/ac/academy.php',  {name: this.name, phone: this.phone, email: this.email})
             .then(response => {
                console.log(response)
             })
             .catch((error) => {
                console.log(error)
                return error;
            })
         },
           
    
     }
}

 
       
         
  

</script>




<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
.v-main-wrapper {
  border: 1px solid green;
   //display: flex;
  //justify-content: center;
  //align-items: center;
 
}
.w-main-wrapper {
  width: 1024px;
  height: 768px;
  border: 1px solid green;
 margin: auto;
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
input:invalid:not(:placeholder-shown) {border-color: red;}
input:valid:not(:placeholder-shown) {border-color: green;}

input[type=text] {

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

</style>