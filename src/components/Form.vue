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
              <form>
                <div class="form-fields">
                    <input
                    class="field"
                    type="text"
                    placeholder="First Name"
                    >
                    <input
                    class="field"
                    type="text"
                    placeholder="Last Name"
                    >
                    <input
                    class="field"
                    type="text"
                    placeholder="Email"
                    >
                    <input
                    class="field"
                    type="text"
                    placeholder="Telephone Number"
                    >
                    <input
                    class="field"
                    type="text"
                    placeholder="Subject"
                    >
                    <textarea
                    class="field text-area"
                    cols="30"
                    rows="10"
                    placeholder="Message"></textarea>
                </div>
              <button class="btn">Send</button>
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

export default {

    data() {
        return {
            year: 0,
            animations: [
                "animate__animated animate__backInLeft",
                "animate__animated animate__backInDown",
                "animate__animated animate__backInUp"
            ]

        }
    },
    computed: {
        
    },
    methods: {
        
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
    cursor: pointer;
    transition: 1s;
}

.field:hover {

    border-color: #0AAC9D;
    color: #0AAC9D;
}
.btn:hover {

    transform: scale(1.1);
}

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
</style>