<template>
  <div ref="back" v-bind:class="class">
    <div class="form">
      <div class="button-box">
        <div ref="btn" id="btn"></div>
        <button type="button" class="toggle-button-l" @click="signUp">
          Регистрация
        </button>
        <button type="button" class="toggle-button-r" @click="signIn">
          Вход
        </button>
      </div>
      <div ref="SI" class="sign-in" v-if="visibleIn">
        <label id="email"
          ><input
            type="text"
            class="in-field"
            v-model="signInForm.email"
            required
          /><span class="moved-span">Почта</span></label
        >
        <label id="password"
          ><input
            type="password"
            class="in-field"
            v-model="signInForm.password"
            required
          /><span class="moved-span">Пароль</span></label
        >
        <div class="right">
          <button type="submit" class="submit-btn" @click="showIn">
            Войти
          </button>
        </div>
      </div>

      <div ref="SU" class="sign-up" v-if="!visibleIn">
        <label id="email"
          ><input
            type="text"
            class="in-field"
            v-model="signUpForm.email"
            required
          /><span class="moved-span">Почта</span></label
        >
        <label id="email"
          ><input
            type="text"
            class="in-field"
            v-model="signUpForm.name"
            required
          /><span class="moved-span">Имя</span></label
        >
        <label id="email"
          ><input
            type="text"
            class="in-field"
            v-model="signUpForm.surname"
            required
          /><span class="moved-span">Фамилия</span></label
        >
        <label id="email"
          ><input
            type="date"
            class="in-field"
            v-model="signUpForm.dateOfBirth"
            required
          /><span class="moved-span-date">Дата рождения</span></label
        >
        <label id="password"
          ><input
            type="password"
            class="in-field"
            v-model="signUpForm.password"
            required
          /><span class="moved-span">Пароль</span></label
        >
        <label id="password"
          ><input
            type="password"
            class="in-field"
            v-model="signUpForm.passwordRep"
            required
          /><span class="moved-span">Повторите пароль</span></label
        >
        <div class="right">
          <button type="submit" class="submit-btn" @click="showUp">
            Присоединиться
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      signInForm: {
        email: "",
        password: "",
      },
      signUpForm: {
        email: "",
        name: "",
        surname: "",
        dateOfBirth: "",
        password: "",
        passwordRep: "",
      },
      visibleIn: true,
      class: "small-back",
    };
  },

  methods: {
    signIn() {
      this.class = "small-back";
      this.visibleIn = true;
      this.$refs.btn.style.left = "50%";
    },
    signUp() {
      this.class = "back";
      this.visibleIn = false;
      this.$refs.btn.style.left = "0%";
    },
    showUp() {
      //функция для регистрации (не реализована, но связана с формой)
      console.log(this.signUpForm); //worked
      this.signUpForm.email = "";
      this.signUpForm.name = "";
      this.signUpForm.surname = "";
      this.signUpForm.dateOfBirth = "";
      this.signUpForm.password = "";
      this.signUpForm.passwordRep = "";
    },
    showIn() {
      //функция для входа (не реализована, но связана с формой)
      console.log(this.signInForm); //worked
      this.signInForm.email = "";
      this.signInForm.password = "";
    },
  },
};
</script>

<style scoped>
:root {
  --white-blue: #b2dff2;
  --brown: #995459;
  --brown-dark: #733f43;
  --brown-trans: rgba(153, 84, 89, 0.5);
  --white-orange: #fba692;
  --white-orange-bright: #fe9882;
  --white-yellow: #fed6a3;
  --white-yellow-bright: #fcc47a;
  --white-yellow-trans: rgba(254, 214, 163, 0.5);
  --white-purple: #ae8a94;
  --white-purple-trans: rgba(174, 138, 148, 0.5);
}

.back {
  position: relative;
  display: grid;
  align-items: center;
  justify-items: center;
  top: 3vh;
  right: 5vw;
  height: 80vh;
  width: 25vw;
  margin-left: 10px;
  margin-bottom: 5px;
  background-color: var(--white-purple-trans);
  border-radius: 40px;
  background-attachment: fixed;
  backdrop-filter: blur(10px);
}

.small-back {
  position: relative;
  display: grid;
  align-items: center;
  justify-items: center;
  top: 3vh;
  right: 5vw;
  height: 45vh;
  width: 25vw;
  margin-left: 10px;
  margin-bottom: 5px;
  background-color: var(--white-purple-trans);
  border-radius: 40px;
  background-attachment: fixed;
  backdrop-filter: blur(10px);
}

.form {
  top: 1vh;
  display: grid;
  width: 85%;
  margin-left: 15%;
  position: relative;
  bottom: 5%;
}

.title {
  font-size: 24px;
  margin-bottom: 16px;
  margin-left: 17%;
  color: #fff;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
}

.sign-in {
  top: 2vh;
  display: grid;
  position: relative;
}

.sign-up {
  top: 2vh;
  display: grid;
  position: relative;
  /*
  width: 40vh;
  top: 7.45vh;
  right: 45vh;
  position: absolute;
  */
}

.button-box {
  margin: 6px auto;
  position: relative;
  border-radius: 30px;
  width: 75%;
  box-shadow: 0 0 20px 9px var(--white-orange-bright);
  right: 10%;
  bottom: 15%;
}

.button-box:active {
  box-shadow: 0 0 20px 9px var(--white-yellow-bright);
}

.toggle-button-l {
  font-size: 18px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  color: white;
  left: 5%;
  cursor: pointer;
  background: transparent;
  border: 0;
  outline: none;
  position: relative;
}

.toggle-button-r {
  font-size: 18px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  color: white;
  padding: 10px 30px;
  cursor: pointer;
  background: transparent;
  border: 0;
  outline: none;
  position: relative;
  left: 13%;
}

.submit-btn {
  width: 50%;
  font-size: 18px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  color: white;
  align-self: left;
  padding: 10px 10px;
  cursor: pointer;
  margin: auto;
  background: linear-gradient(
    to right,
    var(--brown-trans),
    var(--white-purple-trans)
  );
  box-shadow: 0 0 20px 9px var(--white-orange-bright);
  outline: none;
  border: 0;
  border-radius: 30px;
}

.submit-btn:active {
  box-shadow: 0 0 20px 9px var(--white-yellow-bright);
}

#btn {
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
  left: 50%;
  border-radius: 30px;
  background: linear-gradient(to right, var(--brown), var(--white-purple));
  transition: 0.5s;
  position: absolute;
}

.check-box {
  display: flex;
  right: 100px;
  margin: 10px 10px 10px 0;
  background-color: black;
}

.check-group {
  transition: 0.5s;
  display: flex;
  margin: 10px;
}

.in-field {
  height: 50px;
  width: 80%;
  color: #fff;
  border-radius: 10px;
  outline: none;
  padding: 0 16px;
  border-color: var(--white-orange);
  background: none;
  box-shadow: 7px 5px 5px var(--white-orange-bright);
}

.in-field:focus {
  border-color: var(--white-yellow);
  box-shadow: 7px 5px 5px var(--white-yellow-bright);
}

.in-field + .moved-span {
  color: var(--white-yellow);
  font-size: 14px;
  text-align: center;
  font-weight: bold;
  left: 8px;
  top: -9px;
  background-color: var(--white-yellow-bright);
  border-radius: 12px;
  color: var(--brown-dark);
  width: 42%;
}

.in-field + .moved-span-date {
  color: var(--white-yellow);
  font-size: 14px;
  text-align: center;
  font-weight: bold;
  left: 8px;
  top: -9px;
  background-color: var(--white-yellow-bright);
  border-radius: 12px;
  color: var(--brown-dark);
  width: 42%;
}

label {
  position: relative;
  margin-bottom: 16px;
}

.moved-span {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  position: absolute;
  left: 16px;
  top: 30%;
  color: black;
  background: none;
  color: #fff;
  transition: all 0.3s ease-in-out;
  width: 150px;
}

.moved-span-date {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  position: absolute;
  left: 16px;
  top: 30%;
  color: black;
  background: none;
  color: #fff;
  transition: all 0.3s ease-in-out;
  width: 150px;
}

.static-span {
  position: relative;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 100;
  font-size: 16px;
  color: white;
  margin: 10px 10px;
}

.right {
  position: relative;
  left: 18%;
  top: 1vh;
}
</style>
