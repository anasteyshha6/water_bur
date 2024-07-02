<template>
  <section>
    <div class="all_services">
      <div class="head_center">
        <h1>НАШИ УСЛУГИ БУРЕНИЯ СКВАЖИН</h1>
        <h3>ФИЛЬТРЫ ПО УСЛУГАМ</h3>
      </div>
      <div class="requisites">
        <Filter v-model="selectedOpt" :options="options" />

        <main-input
          id="hide"
          placeholder="Введите название услуги"
          v-model="searchValue"
        />
      </div>
      <div class="services">
        <div
          class="cart_service"
          v-for="service in searchService"
          :key="service.title"
        >
          <div class="img">
            <img :src="service.img" :alt="service.title" />
          </div>
          <h3>{{ service.title }}</h3>
          <p>{{ service.description }}</p>
        </div>
      </div>

      <main-button @click="showDialog"
        >РАССЧИТАТЬ СТОИМОСТЬ СКВАЖИНЫ</main-button
      >

      <main-dialog :show="openWindow">
        <main-form @close="closeWin"></main-form>
      </main-dialog>
    </div>
  </section>
</template>

<script>
import MainTitle from "../MainTitle.vue";
import MainButton from "../MainButton.vue";
import MainDialog from "./MainDialog.vue";
import MainForm from "./MainForm.vue";
import MainInput from "../MainInput.vue";
import Filter from "./Filter.vue";

export default {
  components: {
    MainTitle,
    MainButton,
    MainDialog,
    MainForm,
    MainInput,
    Filter,
  },

  data() {
    return {
      services: [
        {
          title: "Бурение бытовых скважин на воду",
          description:
            "Проведение буровых работ для получения чистой воды для дома и дачи.",
          img: "/imgs/work1.svg",
        },
        {
          title: "Монтаж насоса",
          description:
            "Установка насосного оборудования для обеспечения стабильного водоснабжения.",
          img: "/imgs/work2.svg",
        },
        {
          title: "Монтаж насосного оборудования под ключ",
          description:
            "Полный комплекс услуг по установке насосов, включая все необходимые работы и настройки.",
          img: "/imgs/work3.svg",
        },
        {
          title: "Бурение промышленных скважин",
          description:
            "Бурение глубоких скважин для промышленных нужд с использованием специализированного оборудования.",
          img: "/imgs/work4.svg",
        },
      ],
      searchValue: "",
      openWindow: false,
      selectedOpt: "none",
      options: [
        { value: "nameUp", name: 'По возрастанию от "А" до "Я"' },
        { value: "nameDown", name: 'По убыванию от "Я" до "А"' },
      ],
    };
  },

  methods: {
    showDialog() {
      this.openWindow = true;
      document.body.style.overflowY = "hidden";
    },

    closeWin() {
      this.openWindow = false;
      document.body.style.overflowY = "scroll";
    },
  },

  computed: {
    sortedService() {
      if (this.selectedOpt === "nameUp") {
        return [...this.services].sort((ser1, ser2) =>
          ser1.title.localeCompare(ser2.title)
        );
      } else if (this.selectedOpt === "nameDown") {
        return [...this.services].sort((ser1, ser2) =>
          ser2.title.localeCompare(ser1.title)
        );
      } else {
        return [...this.services];
      }
    },

    searchService() {
      if (this.searchValue) {
        return this.sortedService.filter(
          (service) =>
            service.title
              .toLowerCase()
              .includes(this.searchValue.toLowerCase()) ||
            service.description
              .toLowerCase()
              .includes(this.searchValue.toLowerCase())
        );
      }
      return this.sortedService;
    },
  },
};
</script>

<style scoped>
.cart_service h3 {
  color: #01588b;
}
</style>
