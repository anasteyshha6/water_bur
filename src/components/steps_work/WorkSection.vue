<template>
  <section class="blue">
    <div class="container">
      <div class="work" id="work">
        <MainTitle title="КАК ПРОХОДИТ НАША РАБОТА" />
        <WorkStep
          v-for="(step, index) in steps"
          :key="index"
          :imageSrc="step.imageSrc"
          :imageAlt="step.imageAlt"
          :stepTitle="step.stepTitle"
          :stepDescription="step.stepDescription"
        />
      </div>
    </div>
  </section>
</template>
<script>
import MainTitle from "../MainTitle.vue";
import WorkStep from "./WorkStep.vue";

export default {
  components: {
    WorkStep,
    MainTitle,
  },
  data() {
    return {
      steps: [
        {
          imageSrc: "/public/imgs/water.svg",
          imageAlt: "water",
          stepTitle: "1 ЭТАП. ОЦЕНКА МЕСТНОСТИ",
          stepDescription:
            "Наша команда специалистов проводит тщательную оценку местности, чтобы определить наилучшее место для бурения скважины, учитывая геологические особенности и потребности клиента.",
        },
        {
          imageSrc: "/public/imgs/water.svg",
          imageAlt: "water",
          stepTitle: "2 ЭТАП. ПОДГОТОВКА ОБОРУДОВАНИЯ",
          stepDescription:
            "Мы используем современное оборудование и технологии для проведения бурения скважин, что позволяет нам обеспечить высокую эффективность и точность работ.",
        },
        {
          imageSrc: "/public/imgs/water.svg",
          imageAlt: "water",
          stepTitle: "3 ЭТАП. БУРЕНИЕ СКВАЖИН",
          stepDescription:
            "Наша бригада осуществляет бурение скважин с соблюдением всех технических и безопасностных стандартов, чтобы обеспечить надежное водоснабжение для клиентов.",
        },
        {
          imageSrc: "/public/imgs/water.svg",
          imageAlt: "water",
          stepTitle: "4 ЭТАП. ТЕХНИЧЕСКОЕ ОБСЛУЖИВАНИЕ",
          stepDescription:
            "После завершения работ, мы предоставляем клиентам техническое обслуживание и консультации по эксплуатации скважины, чтобы обеспечить долгосрочную надежность системы водоснабжения.",
        },
        {
          imageSrc: "/public/imgs/water.svg",
          imageAlt: "water",
          stepTitle: "5 ЭТАП. ГАРАНТИЯ КАЧЕСТВА",
          stepDescription:
            "Мы гарантируем высокое качество услуг и удовлетворение потребностей каждого клиента.",
        },
      ],
    };
  },
};
</script>
<style scoped></style>
