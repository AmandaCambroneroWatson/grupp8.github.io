<template>
  <form>
    <!--MOBILE-->
    <div class="Mobilecontainer">
      <h1>Sign up</h1>
      <input type="text" placeholder="Name" />
      <input type="text" placeholder="Email" v-model="email" required />
      <br />
      <span class="span-validation" v-if="message.email">{{
        message.email
      }}</span>
      <input
        type="password"
        placeholder="Password"
        v-model="password"
        required
      /><br />
      <span class="span-validation" v-if="message.password">{{
        message.password
      }}</span>
      <input
        type="submit"
        value="Sign up"
        class="signinbutton"
        @click="goToLogin()"
      />
    </div>
    <!--MOBILE-->
    <!--------------------------->
    <!--Desktop-->
    <div class="Desktopcontainer">
      <h1 class="LoginHeader">Sign up</h1>
      <div class="inputs">
        <input type="text" placeholder="Name" />
        <input type="text" placeholder="Email" v-model="email" required />
        <br />
        <span class="span-validation" v-if="message.email">{{
          message.email
        }}</span>
        <input
          type="password"
          placeholder="Password"
          v-model="password"
          required
        /><br />
        <span class="span-validation" v-if="message.password">{{
          message.password
        }}</span>
        <p class="AlreadyHaveAccount">Already Have an account?</p>
      </div>
      <input
        type="submit"
        value="Sign up"
        class="signinbutton"
        @click="goToLogin()"
      />
    </div>
    <div class="circles"></div>
    <div class="stripes"></div>
  </form>
</template>

<script>
  export default {
    name: 'SignUp',
    data() {
      return {
        password: '',
        email: '',
        message: []
      }
    },
    watch: {
      password(value) {
        this.password = value
        this.PasswordValidation(value)
      },
      email(value) {
        this.email = value
        this.EmailValidation(value)
      }
    },
    methods: {
      EmailValidation(value) {
        if (/^\w+([-]?\w+)*@\w+([-]?\w+)*(\w{2,3})+$/.test(value)) {
          this.message['email'] = 'Required'
        } else {
          this.message['email'] = 'Please, enter a valid email'
        }
      },
      PasswordValidation(value) {
        
        if (value.length < 8) {
          this.message['password'] =
            'Your password needs to be 8 characters'
        } else {
          this.message['password'] = 'Required'
        }
      },
      goToLogin() {
        this.$router.push('/login')
      }
    }
  }
</script>

<style>
  body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background-color: #fff;
  }
  p {
    font-style: normal;
    font-weight: 600;
    font-size: 14px;
    line-height: 19px;
    color: #5db075;
  }

  * {
    box-sizing: border-box;
  }

  /* Add padding to containers */
  .Mobilecontainer {
    padding: 16px;
    background-color: #fff;
  }

  /* Full-width input fields */
  input[type='text'],
  input[type='password'] {
    width: 100%;
    padding: 15px;
    margin: 5px 0 22px 0;
    display: inline-block;
    border: 1px solid #e8e8e8;
    box-sizing: border-box;
    border-radius: 8px;
    background: #f6f6f6;
    font-style: normal;
    font-weight: 600;
    font-size: 14px;
    line-height: 19px;
    color: #bdbdbd;
  }

  /* Set a style for the submit button */
  .signinbutton {
    background-color: #5db075;
    color: #fff;
    padding: 16px 32px;
    margin: 8px 0;
    border: none;
    cursor: pointer;
    width: 100%;
    opacity: 0.9;
    border-radius: 25px;
  }

  .span-validation {
    display: flex;
    flex-direction: column;
    align-self: flex-start;
    font-style: normal;
    font-weight: 600;
    font-size: 14px;
    line-height: 19px;
    color: #ED2121;
    padding-top: 0px;
    margin-top: 0px;
  }
  input[type='submit'] {
    font-style: normal;
    font-weight: 600;
    font-size: 14px;
    text-align: center;
    line-height: 19px;
  }
  .registerbtn:hover {
    opacity: none;
  }
  .Desktopcontainer {
    display: none;
  }
  @media only screen and (min-device-width: 1000px) {
    .Mobilecontainer {
      display: none;
    }
    .Desktopcontainer {
      display: block;
      width: 514px;
      height: 514px;
      margin-left: 38%;
      margin-top: 10%;
      background-color: rgb(255, 255, 255);
      border-radius: 20px;
      box-shadow: 0px 0px 20px 5px rgba(0, 0, 0, 0.21);
    }

    input[type='text'],
    input[type='password'] {
      width: 343px;
      padding: 15px;
      margin: 5px 0 22px 0;
      display: inline-block;
      border: 1px solid #e8e8e8;
      box-sizing: border-box;
      border-radius: 8px;
      background: #f6f6f6;
      font-style: normal;
      font-weight: 600;
      font-size: 14px;
      line-height: 19px;
      color: #bdbdbd;
    }
    .signinbutton {
      background-color: #5db075;
      color: #fff;
      padding: 16px 32px;
      margin: 8px 0;
      border: none;
      cursor: pointer;
      width: 343px;
      opacity: 0.9;
      border-radius: 25px;
      margin-top: 46px;
    }
    .LoginHeader {
      padding: 25px;
    }

    .AlreadyHaveAccount {
      margin-top: -10px;
    }
    .circles {
      background-image: Url('~@/assets/Circles.png');
      width: 268px;
      height: 500px;
      position: absolute;
      right: 0;
      top: 15%;
      background-repeat: no-repeat;
    }
    .stripes {
      background-image: Url('~@/assets/Stripes.png');
      width: 400px;
      height: 445px;
      position: absolute;
      left: 0%;
      bottom: 0%;
      background-repeat: no-repeat;
    }
  }

  /* ----------- iPhone 6+, 7+ and 8+ ----------- */

  /* Portrait and Landscape */
  @media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (-webkit-min-device-pixel-ratio: 3) {
  }

  /* Portrait */
  @media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (-webkit-min-device-pixel-ratio: 3) and (orientation: portrait) {
  }

  /* Landscape */
  @media only screen and (min-device-width: 414px) and (max-device-width: 736px) and (-webkit-min-device-pixel-ratio: 3) and (orientation: landscape) {
  }
</style>
