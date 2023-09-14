<template>
  <form @submit.prevent="$emit('getValidDate', ageResult)">
    <Input
      :classes="validate"
      v-model:model-value="birth.day"
      title="DAY"
      place-h="DD"
      :error="errorDay"
      error-message="Must be a valid Day"
    />
    <Input
      :classes="validate"
      v-model:model-value="birth.month"
      title="MONTH"
      place-h="MM"
      :error="errorMonth"
      error-message="Must be a valid month"
    />
    <Input
      :classes="validate"
      v-model:model-value="birth.year"
      title="YEAR"
      place-h="YYYY"
      :error="errorYear"
      error-message="Must be a in the past"
      element-title="value between 1900 - this year"
    />
    <Button @create-output="calculateAge(birth)" />
  </form>
</template>

<script setup>
import { computed, ref } from "vue";
import Input from "./Input.vue";
import Button from "./Button.vue";

defineEmits(["getValidDate"]);

const birth = ref({
  day: null,
  month: null,
  year: null,
});
const valid = ref(true);
const ageResult = ref(null);

const getLastDay = (mm, yyyy) => {
  const lastDay = new Date(yyyy, mm + 1, 0);
  return lastDay.getDate();
};

const validate = computed(() => {
  return valid.value ? "" : "error";
});

const errorDay = computed(() => {
  const lastday = getLastDay(birth.value.month, birth.value.year);
  if (birth.value.day > lastday || birth.value.day < 1) {
    return true;
  } else {
    return false;
  }
});

const errorMonth = computed(() => {
  if (birth.value.month < 1 || birth.value.month > 12) {
    return true;
  } else {
    return false;
  }
});

const errorYear = computed(() => {
  const today = new Date();
  const thisYear = today.getFullYear();

  if (birth.value.year > thisYear || birth.value.year < 1900) {
    return true;
  } else {
    return false;
  }
});


const isValid = (obj) => {
  const lastday = getLastDay(obj.month, obj.year);
  const today = new Date();
  const thisYear = today.getFullYear();

  if (
    obj.day === "" ||
    obj.day === null ||
    obj.month === "" ||
    obj.month === null ||
    obj.year === "" ||
    obj.year === null
  ) {
    valid.value = false;
    return false;
  } else if (obj.day < 1 || obj.month < 1 || obj.year < 1) {
    console.log("must be a positive number");
    valid.value = false;
    return false;
  } else if (obj.day > lastday) {
    console.log("select a valid day");
    valid.value = false;
    return false;
  } else if (obj.year > thisYear || obj.year < 1900) {
    console.log("select a valid year");
    valid.value = false;
    return false;
  } else if (obj.month > 12) {
    console.log("select a valid month");
    valid.value = false;
    return false;
  } else {
    valid.value = true;
    return true;
  }
};


const calculateAge = (obj) => {
  const birthdate = new Date(`${obj.year}-${obj.month}-${obj.day}`); // yyyy-mm-dd
  const today = new Date();

  if (!isValid(obj)) {
    return;
  }

  let yearsOld = today.getFullYear() - birthdate.getFullYear();
  let monthsOld = today.getMonth() - birthdate.getMonth();
  let daysOld = today.getDate() - birthdate.getDate();

  if (daysOld > getLastDay(today.getMonth(), today.getFullYear())) {
    daysOld =
      getLastDay(today.getMonth(), today.getFullYear()) - Math.abs(daysOld) + 1;
    monthsOld++;
  }
  if (daysOld < 0) {
    monthsOld--;
    daysOld =
      getLastDay(today.getMonth(), today.getFullYear()) - Math.abs(daysOld) + 1;
  }
  if (monthsOld >= 12) {
    monthsOld = Math.abs(monthsOld) - 12;
    yearsOld++;
  }
  if (monthsOld < 0) {
    monthsOld = 12 - Math.abs(monthsOld);
    yearsOld--;
  }
  ageResult.value = { day: daysOld, month: monthsOld, year: yearsOld };
};
</script>

<style>
form {
  display: grid;
  position: relative;
  grid-template-columns: repeat(4, 1fr);
  grid-row: 1 / 2;
}

@media (max-width: 768px) {
  form {
    grid-template-columns: repeat(3, 1fr);
  }
}
@media (max-width: 480px) {
  form {
    gap: 5px;
  }
}
</style>