<template>
  <div class="container">
      <div class="container-form">
          <div class="container-title" :class="animations[1]">
              <h1>Form Validation Example VueJs</h1>
          </div>
          <div class="form-info" :class="animations[0]">
              <div class="form-title">
                  <h3>Contact Us</h3>
              </div>
               <div class="form-legend">
                  <p>Fillout the form bellow to know more</p>
              </div>
              <form @submit.prevent="validateForm">
                <div class="form-fields">
                    <div class="field-icon">
                       <input
                        class="field"
                        type="text"
                        placeholder="First Name"
                        v-model.trim="form.firstName"
                        v-on:keyup="validarCampoFirstName"
                        :class="validations.firstName"
                        >
                        <box-icon
                        :name='icons[0].name'
                        :color = 'icons[0].color'
                        size="xs" ></box-icon>
                   </div>
                   <div class="field-icon">
                        <input
                        class="field"
                        type="text"
                        placeholder="Last Name"
                        v-model.trim="form.lastName"
                        v-on:keyup="validarCampoLastName"
                        :class="validations.lastName"
                        >
                        <box-icon
                        :name='icons[1].name'
                        :color = 'icons[1].color'
                        size="xs" ></box-icon>
                   </div>
                   <div class="field-icon">
                        <input
                        class="field"
                        type="text"
                        placeholder="Email"
                        v-model.trim="form.email"
                        v-on:keyup="validarCampoEmail"
                        :class="validations.email"
                        >
                        <box-icon
                        :name='icons[2].name'
                        :color = 'icons[2].color'
                        size="xs" ></box-icon>
                   </div>
                   <div class="field-icon">
                       <input
                        class="field"
                        type="text"
                        placeholder="Telephone Number"
                        v-model.trim="form.telephoneNumber"
                        v-on:keyup="validarCampoTelephoneNumber"
                        :class="validations.telephoneNumber"
                        >
                        <box-icon
                        :name='icons[3].name'
                        :color = 'icons[3].color'
                        size="xs" ></box-icon>
                   </div>
                    <div class="field-icon">
                        <input
                        class="field"
                        type="text"
                        placeholder="Subject"
                        v-model.trim="form.subject"
                        v-on:keyup="validarCampoSubject"
                        :class="validations.subject"
                        >
                        <box-icon
                        :name='icons[4].name'
                        :color = 'icons[4].color'
                        size="xs" ></box-icon>
                    </div>
                    <div class="field-icon">
                        <textarea
                        class="field text-area"
                        cols="30"
                        rows="10"
                        placeholder="Message"
                        v-model.trim="form.message"
                        v-on:keyup="validarCampoMessage"
                        :class="validations.message"></textarea>
                        <box-icon
                        :name='icons[5].name'
                        :color = 'icons[5].color'
                        size="xs" ></box-icon>
                    </div>
                    
                </div>
              <button class="btn" :disabled="blockBtn" :class="opacityBtn">Send</button>
              </form>
          </div>
      </div>
      <footer id="form-footer" :class="animations[2]">
          <p>&copy;{{year}} Example Form Validation in VueJs | Design by Enrique Velasco</p>
      </footer>
  </div>
</template>

<script>
import animate__backInLeft from 'animate.css'
import animate__backInDown from 'animate.css'
import animate__backInUp from 'animate.css'

import Swal from 'sweetalert2'
import 'boxicons'


export default {

    data() {
        return {
            year: 0,
            animations: [
                "animate__animated animate__backInLeft",
                "animate__animated animate__backInDown",
                "animate__animated animate__backInUp"
            ],
            form: {
                firstName: '',
                lastName: '',
                email: '',
                telephoneNumber: '',
                subject: '',
                message: ''
            },
            validations: {
                firstName: '',
                lastName: '',
                email: '',
                telephoneNumber: '',
                subject: '',
                message: ''
            },
            icons: [
                {name: '', color: ''},
                {name: '', color: ''},
                {name: '', color: ''},
                {name: '', color: ''},
                {name: '', color: ''},
                {name: '', color: ''},
            ]

        }
    },
    computed: {
        blockBtn() {

            const { firstName, lastName, email, telephoneNumber, subject, message } = this.form;
            return !firstName || !lastName || !email || !telephoneNumber || !subject || !message 
        },
        opacityBtn() {

            const { firstName, lastName, email, telephoneNumber, subject, message } = this.validations;
            const arrayValidations = [firstName, lastName, email, telephoneNumber, subject, message ];

            //Validar campo a campo
            let isValid;
            isValid = arrayValidations.some( item => item === 'error' || item === "");
            return isValid ? 'btn-block' : 'btn-no-block'
        },
       
        
         
    },
    methods: {
        validateForm() {
            
             
        },
        validarCampoFirstName() {

            const { firstName } = this.form;
            
            if( firstName.length < 3) {
                this.validations.firstName = 'error';
                this.icons[0].name = 'x';
                this.icons[0].color = 'red';

            } else {
                this.validations.firstName = 'success';
                this.icons[0].name = 'check';
                this.icons[0].color = 'green';
            }
        },
        validarCampoLastName() {

            const { lastName } = this.form;
            
            if( lastName.length < 3) {
                this.validations.lastName = 'error';
                this.icons[1].name = 'x';
                this.icons[1].color = 'red';
            } else {
                this.validations.lastName = 'success';
                this.icons[1].name = 'check';
                this.icons[1].color = 'green';
            }
        },
        validarCampoEmail() {

            const { email } = this.form;
            const regex = /^(([^<>()[\]\.,;:\s@\"]+(\.[^<>()[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i;
            
            if( regex.test(email) ) {
                this.validations.email = 'success';
                this.icons[2].name = 'check';
                this.icons[2].color = 'green';
            } else {
                this.validations.email = 'error';
                this.icons[2].name = 'x';
                this.icons[2].color = 'red';
            }
        },
        validarCampoTelephoneNumber() {

            const { telephoneNumber } = this.form;
            
            if( telephoneNumber.length !== 10) {
                this.validations.telephoneNumber = 'error';
                this.icons[3].name = 'x';
                this.icons[3].color = 'red';
            } else {
                this.validations.telephoneNumber = 'success';
                this.icons[3].name = 'check';
                this.icons[3].color = 'green';
            }
        },
        validarCampoSubject() {

            const { subject } = this.form;
            
            if( subject.length < 3) {
                this.validations.subject = 'error';
                this.icons[4].name = 'x';
                this.icons[4].color = 'red';
            } else {
                this.validations.subject = 'success';
                this.icons[4].name = 'check';
                this.icons[4].color = 'green';
            }
        },
        validarCampoMessage() {

            const { message } = this.form;
            
            if( message.length < 3) {
                this.validations.message = 'error';
                this.icons[5].name = 'x';
                this.icons[5].color = 'red';
            } else {
                this.validations.message = 'success';
                this.icons[5].name = 'check';
                this.icons[5].color = 'green';
            }
        },
        
        
    },
    created() {

        this.year = new Date().getFullYear();
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@300&family=Roboto&display=swap');

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.container {

    width: 100%;
    height: 90vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;

}
.container-form {

    width: 70%;
    color: black;
    font-family: 'Roboto', sans-serif;
    text-align: center;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;

}
.container-title {

    width: 80%;
    margin-bottom: 50px;
    font-size: 30px;
    color: rgb(76, 208, 196);

}
.form-info {

    width: 50%;
    border-radius: 10px;
    box-shadow: 0px 0px 60px rgba(76, 208, 196, 0.3);
    padding: 35px;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
}
.form-title {

    width: 80%;
    font-size: 25px;
    margin-bottom: 15px;

}
.form-legend p {

    font-size: 17px;
    margin-bottom: 25px;
}
form {

    width: 80%;
}
.form-fields {

    width: 100%;
}
.field-icon {

    width: 100%;
    display: flex;
    justify-content: space-between;
}
.field {

    width: 95%;  
    margin-bottom: 10px;
    height: 40px;
    padding: 10px 15px;
    outline: none;
    border-color: transparent;
    border-radius: 10px;
    font-family: 'Hind Siliguri', sans-serif;
    
}
.field-icon:last-child {

    height: 120px;
    margin-bottom: 25px;
}
.text-area {
    
    height: 100%;
}
#form-footer {

    width: 80%;
}
.btn {
    width: 60%;
    padding: 10px;
    background-color: #4AFBDB;
    color: #fff;
    outline: none;
    border: transparent;
    border-radius: 40px;
    font-size: 15px;
    transition: 1s;
}

.field:hover {

    border-color: rgb(200, 206, 204 );
    color: #000;
}
/* .btn:hover {

    transform: scale(1.1);
} */

@media screen and (max-width: 1024px) {

    .container-title {

        font-size: 15px;

    }
    .form-info {

    width: 80%;

    }
    .form-title {

        width: 80%;
        font-size: 20px;
        margin-bottom: 15px;

    }
    .form-legend p {

        font-size: 15px;
        margin-bottom: 20px;

    }
}

@media screen and (max-width: 700px) {

    .container-title {

        font-size: 8px;
        margin-bottom: 10px;

    }
    .container-form {

        width: 90%;
    }
    .form-info {

        width: 100%;
        margin-bottom: 20px;

    }
    .form-title {

        width: 80%;
        font-size: 15px;
        margin-bottom: 20px;

    }
    .form-legend p {

        font-size: 12px;
        margin-bottom: 20px;

    }
    form {

        width: 100%;
    }
    .btn {
    
        font-size: 12px;
    }
    #form-footer {

        width: 95%;
        font-size: 12px;
        margin-bottom: 20px;
    }
}

.btn-block {
    opacity: 0.2;
    cursor: none;
}
.btn-no-block {
    opacity: 1;
    cursor: pointer;
}

/* errors */
.error {
    
    border: 1px solid rgb(248, 153, 163);
    box-shadow: 0px 0px 2px 2px rgba(241, 61, 80, 0.3);
    
}
.success {
    
    border: 1px solid rgb(190, 240, 130);
    box-shadow: 0px 0px 2px 2px rgba(139, 240, 19, 0.3);
}

</style>