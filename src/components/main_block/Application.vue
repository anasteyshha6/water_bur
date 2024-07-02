<template>
  <div class="application">
    <h1>Оставьте заявку на сайте и мы Вам перезвоним!</h1>
    <form action="" @submit.prevent="onSubmit">
      <label>Введите имя</label>
      <input
        :class="{ 'input-error': errorName }"
        class="str"
        placeholder="Имя"
        type="text"
        v-model="user_name"
        @input="clearErrorName"
      />
      <p v-if="errorName" class="errorMes">{{ errorName }}</p>
      <label>Введите номер телефона</label>
      <input
        :class="{ 'input-error': errorPhone }"
        class="str"
        placeholder="Номер телефона"
        type="text"
        v-model="user_phone"
        @input="clearErrorPhone"
      />
      <p v-if="errorPhone" class="errorMes">{{ errorPhone }}</p>
      <label>Введите E-mail</label>
      <input
        :class="{ 'input-error': errorEmail }"
        class="str"
        placeholder="E-mail"
        type="email"
        v-model="user_email"
        @input="clearErrorEmail"
      />
      <p v-if="errorEmail" class="errorMes">{{ errorEmail }}</p>
      <main-button>Отправить</main-button>
    </form>
    <div class="agree">
      <p>
        Нажимая на кнопку "Отправить", Вы принимаете
        <span class="link">Положение</span> и
        <span class="link">Согласие на обработку персональных данных.</span>
      </p>
    </div>
  </div>
</template>

<script>
import MainButton from "../MainButton.vue";
import axios from "axios";

export default {
  components: {
    MainButton,
  },

  data() {
    return {
      user_name: "",
      user_phone: "",
      user_email: "",
      errorName: "",
      errorPhone: "",
      errorEmail: "",
    };
  },

  methods: {
    async onSubmit() {
      this.clearErrorMes();

      if (!this.user_name || !this.user_phone || !this.user_email) {
        if (!this.user_name) {
          this.errorName = "Имя должно быть заполнено";
        }
        if (!this.user_phone) {
          this.errorPhone = "Номер телефона должен быть заполнен";
        }
        if (!this.user_email) {
          this.errorEmail = "Email должен быть заполнен";
        }
        return;
      }

      const namePattern = /^[а-яА-ЯЁё]+$/;
      if (!namePattern.test(this.user_name)) {
        this.errorName = "Имя должно содержать только русские буквы";
        return;
      }

      try {
        const response = await axios.post("http://localhost:3000/email", {
          name: this.user_name,
          phoneNum: this.user_phone,
          email: this.user_email,
        });
        console.log(response.data);
        alert(
          "Ваша заявка успешно отправлена! В ближайшее время с Вами свяжутся!"
        );
        this.clearForm();
      } catch (error) {
        console.error("There was an error sending the email:", error);
        alert(
          "Заявка не отправлена..."
        );
        this.clearForm();
      }
    },

    clearForm() {
      this.user_name = "";
      this.user_phone = "";
      this.user_email = "";
    },

    clearErrorMes() {
      this.errorName = "";
      this.errorPhone = "";
      this.errorEmail = "";
    },

    clearErrorName() {
      this.errorName = "";
      if (this.user_name && !/^[а-яА-ЯЁё]+$/.test(this.user_name)) {
        this.errorName = "Имя должно содержать только русские буквы";
      }
    },

    clearErrorPhone() {
      this.errorPhone = "";
    },

    clearErrorEmail() {
      this.errorEmail = "";
    },
  },
};
</script>

<style scoped>
.errorMes {
  color: #ed663b;
  padding-top: 10px;
}

.input-error {
  border: 2px solid #ed663b;
}
</style>
