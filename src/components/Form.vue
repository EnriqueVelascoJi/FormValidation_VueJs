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
                    <input
                    class="field"
                    type="text"
                    placeholder="First Name"
                    v-model.trim="form.firstName"
                    v-on:keyup="validarCampoFirstName"
                    :class="validations.firstName"
                    >
                    <input
                    class="field"
                    type="text"
                    placeholder="Last Name"
                    v-model.trim="form.lastName"
                    v-on:keyup="validarCampoLastName"
                    :class="validations.lastName"
                    >
                    <input
                    class="field"
                    type="text"
                    placeholder="Email"
                    v-model.trim="form.email"
                    v-on:keyup="validarCampoEmail"
                    :class="validations.email"
                    >
                    <input
                    class="field"
                    type="text"
                    placeholder="Telephone Number"
                    v-model.trim="form.telephoneNumber"
                    v-on:keyup="validarCampoTelephoneNumber"
                    :class="validations.telephoneNumber"
                    >
                    <input
                    class="field"
                    type="text"
                    placeholder="Subject"
                    v-model.trim="form.subject"
                    v-on:keyup="validarCampoSubject"
                    :class="validations.subject"
                    >
                    <textarea
                    class="field text-area"
                    cols="30"
                    rows="10"
                    placeholder="Message"
                    v-model.trim="form.message"
                    v-on:keyup="validarCampoMessage"
                    :class="validations.message"></textarea>
                </div>
              <button class="btn" :disabled="blockBtn" :class="opacityBtn">Send</button>
              </form>
          </div>
      </div>
      <footer id="form-footer" :class="animations[2]">
          <p>&copy;{{year}} Example Form Validation in VueJs | Design by Enrique Velasco</p>
      </footer>
  </div>
  {{ form }}
</template>

<script>
import animate__backInLeft from 'animate.css'
import animate__backInDown from 'animate.css'
import animate__backInUp from 'animate.css'

import Swal from 'sweetalert2'

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
            }

        }
    },
    computed: {
        blockBtn() {

            const { firstName, lastName, email, telephoneNumber, subject, message } = this.form;
            return !firstName || !lastName || !email || !telephoneNumber || !subject || !message 
        },
        opacityBtn() {

            const { firstName, lastName, email, telephoneNumber, subject, message } = this.validations;
            return firstName === 'error' || firstName === '' ||
                    lastName === 'error' || lastName === '' ||
                    email === 'error' || email === '' ||
                    telephoneNumber === 'error' || telephoneNumber === '' ||
                    subject === 'error' || subject === '' ||
                    message === 'error' || message === '' ? 'btn-block' : 'btn-no-block'
        },
       
        
         
    },
    methods: {
        // validateForm() {
        //     const { firstName, lastName, email, telephoneNumber, subject, message } = this.form;
        //     console.log(firstName, lastName, email, telephoneNumber, subject, message);

        //     //Creamos el objeto de validación
        //     const regex = {
        //         email: /^(([^<>()[\]\.,;:\s@\"]+(\.[^<>()[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i,

        //     }

        //     if (firstName.length > 3 || firstName.length > 3) {
        //         this.flag = true;
        //     } else if (regex.email.test(email)) {
        //         this.flag = true;
        //     } else if (telephoneNumber.length === 10) {
        //         this.flag = true;
        //     } else if(subject === )
             
        // }
        validarCampoFirstName() {

            const { firstName } = this.form;
            
            if( firstName.length < 3) {
                this.validations.firstName = 'error';
            } else {
                this.validations.firstName = 'success';
            }
        },
        validarCampoLastName() {

            const { lastName } = this.form;
            
            if( lastName.length < 3) {
                this.validations.lastName = 'error';
            } else {
                this.validations.lastName = 'success';
            }
        },
        validarCampoEmail() {

            const { email } = this.form;
            const regex = /^(([^<>()[\]\.,;:\s@\"]+(\.[^<>()[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i;
            
            if( regex.test(email) ) {
                this.validations.email = 'error';
            } else {
                this.validations.email = 'success';
            }
        },
        validarCampoTelephoneNumber() {

            const { telephoneNumber } = this.form;
            
            if( telephoneNumber.length !== 10) {
                this.validations.telephoneNumber = 'error';
            } else {
                this.validations.telephoneNumber = 'success';
            }
        },
        validarCampoSubject() {

            const { subject } = this.form;
            
            if( subject.length < 3) {
                this.validations.subject = 'error';
            } else {
                this.validations.subject = 'success';
            }
        },
        validarCampoMessage() {

            const { message } = this.form;
            
            if( message.length < 3) {
                this.validations.message = 'error';
            } else {
                this.validations.message = 'success';
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
    margin-bottom: 0px;

}
.field {

    width: 100%;  
    margin-bottom: 10px;
    height: 40px;
    padding: 10px 15px;
    outline: none;
    border-color: transparent;
    border-radius: 10px;
    font-family: 'Hind Siliguri', sans-serif;
    
}
.text-area {
    
    height: 120px;
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

    border-color: #0AAC9D;
    color: #0AAC9D;
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
    
    border: 3px solid red;
}
.success {
    
    border: 3px solid green;
}

</style>