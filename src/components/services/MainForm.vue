<template>
  <div style="justify-content: flex-end">
    <main-button class="close_btn" @click="closeWin">
      <img src="/public/imgs/cross.svg" alt="cross" />
    </main-button>
  </div>
  <div class="head_center">
    <h3>РАССЧЕТ СТОИМОСТИ СКВАЖИНЫ</h3>
  </div>

  <p>
    С помощью калькулятора Вы можете
    <span style="font-weight: 600">приблизительно</span> оценить стоимость работ
    по бурению и обустройству скважины в своем районе, в зависимости от
    предполагаемой глубины залегания водоносного слоя.
  </p>

  <form @submit.prevent="calculateSumm">
    <div>
      <label for="area">Выберите район</label>
      <select v-model="selectedArea" id="area">
        <option value="">Не выбрано</option>
        <option value="bor">Борский район</option>
        <option value="vos">Воскресенский район</option>
        <option value="gor">Городецкий район</option>
        <option value="kov">Ковернинский район</option>
        <option value="sem">Семеновский район</option>
        <option value="chkal">Чкаловский район</option>
      </select>
    </div>

    <div>
      <label for="layer">Средняя глубина водоносного слоя</label>
      <p class="calculation" id="layer">{{ layerDepth }}</p>
    </div>

    <div>
      <label for="depth">Введите требуемую глубину (до 100 м)</label>
      <main-input id="depth" v-model="userDepth" />
    </div>

    <div>
      <label>Тип обустройства скважины</label>
      <div class="radio_btn">
        <div style="gap: 10px">
          <input
            type="radio"
            value="no_need"
            name="radio"
            v-model="selectedType"
          />
          <label for="no_need" style="color: black; font-weight: 400"
            >Обустройство не нужно</label
          >
        </div>
        <div style="gap: 10px">
          <input
            type="radio"
            value="summer"
            name="radio"
            v-model="selectedType"
          />
          <label for="summer" style="color: black; font-weight: 400"
            >Упрощенное (летнее)</label
          >
        </div>
        <div style="gap: 10px">
          <input
            type="radio"
            value="full"
            name="radio"
            v-model="selectedType"
          />
          <label for="full" style="color: black; font-weight: 400"
            >Полное (всесезонное)</label
          >
        </div>
      </div>
    </div>

    <div style="justify-content: center; gap: 10px">
      <main-button class="btn_calc" type="submit">Рассчитать</main-button>
      <main-button type="submit" class="clear" @click="clearFilters"
        >Сбросить</main-button
      >
    </div>

    <div>
      <label>Общая стоимость</label>
      <p class="calculation" id="summa">
        {{ total > 0 ? formattedTotal : "Требуется расчет" }}
      </p>
    </div>
  </form>
</template>

<script>
import MainButton from "../MainButton.vue";
import MainInput from "../MainInput.vue";

export default {
  components: {
    MainInput,
    MainButton,
  },

  data() {
    return {
      selectedArea: "",
      userDepth: "",
      total: 0,
      selectedType: "",
      optionArea: {
        sem: "40 м",
        vos: "30 м",
        bor: "25 м",
        gor: "25 м",
        chkal: "45 м",
        kov: "20 м",
      },
    };
  },

  methods: {
    closeWin() {
      this.$emit("close");
    },

    calculateSumm() {
      this.total = 0;
      const depth = parseFloat(this.userDepth);
      if (this.selectedArea === "bor") {
        if (depth > 0 && depth <= 50) {
          this.total += 2200 * depth;
        } else if (depth > 51 && depth <= 80) {
          this.total += 2400 * depth;
        } else if (depth > 81 && depth <= 100) {
          this.total += 2600 * depth;
        }
      } else if (this.selectedArea === "vos" || this.selectedArea === "kov") {
        if (depth > 0 && depth <= 50) {
          this.total += 2500 * depth;
        } else if (depth > 51 && depth <= 80) {
          this.total += 2700 * depth;
        } else if (depth > 81 && depth <= 100) {
          this.total += 2900 * depth;
        }
      } else if (this.selectedArea === "gor") {
        if (depth > 0 && depth <= 50) {
          this.total += 2300 * depth;
        } else if (depth > 51 && depth <= 80) {
          this.total += 2500 * depth;
        } else if (depth > 81 && depth <= 100) {
          this.total += 2700 * depth;
        }
      } else if (this.selectedArea === "sem" || this.selectedArea === "chkal") {
        if (depth > 0 && depth <= 50) {
          this.total += 2400 * depth;
        } else if (depth > 51 && depth <= 80) {
          this.total += 2600 * depth;
        } else if (depth > 81 && depth <= 100) {
          this.total += 2800 * depth;
        }
      }

      if (this.selectedType === "summer") {
        if (depth > 0 && depth <= 40) {
          this.total += 30000;
        } else if (depth >= 41 && depth <= 60) {
          this.total += 40000;
        } else if (depth >= 61 && depth <= 80) {
          this.total += 50000;
        } else if (depth >= 81 && depth <= 100) {
          this.total += 70000;
        }
      } else if (this.selectedType === "full") {
        if (depth > 0 && depth <= 40) {
          this.total += 70000;
        } else if (depth >= 41 && depth <= 60) {
          this.total += 80000;
        } else if (depth >= 61 && depth <= 80) {
          this.total += 90000;
        } else if (depth >= 81 && depth <= 100) {
          this.total += 120000;
        }
      }
    },

    clearFilters() {
      (this.selectedArea = ""), (this.userDepth = ""), (this.selectedType = "");
    },
  },

  computed: {
    layerDepth() {
      return this.optionArea[this.selectedArea] || "Требуется расчет";
    },

    formattedTotal() {
      return this.total.toLocaleString('ru-RU');
    }
  },
};
</script>

<style scoped>
.close_btn {
  margin: 0;
  background: none;
  cursor: pointer;
  padding: 0;
}

.head_center h3 {
  font-family: "Gol", sans-serif;
  font-weight: 700;
  color: #01588b;
  font-size: clamp(1.25rem, 1.2rem + 0.25vw, 1.5rem);
  padding-bottom: 10px;
}

form {
  display: flex;
  flex-direction: column;
  font-family: "Ral", sans-serif;
  gap: 20px;
}

label {
  color: #01588b;
  font-size: 1rem;
  padding: 12px 0;
  font-weight: 600;
}

div {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.calculation {
  width: 200px;
  padding: 10px;
  background-color: #e2eef5;
  color: #6298ba;
  font-size: 1rem;
  border-radius: 12px;
}

select {
  width: 200px;
  border-radius: 12px;
  background-color: white;
  border: 1px solid grey;
  padding: 10px;
  font-family: "Ral", sans-serif;
  color: black;
  font-size: 1rem;
}

.radio_btn {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.btn_calc {
  width: 200px;
  background: #0090e5 50%;
}

.btn_calc:hover {
  background: #0091e5b8 50%;
}

.clear {
  width: 200px;
  background: #6298ba;
}

.clear:hover {
  background: rgba(72, 111, 136, 0.593);
}
</style>
