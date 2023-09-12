<template>
  <a-form class="form">
    <a-form-item label="DAY" :colon="false" class="form__item">
      <a-input
        placeholder="DD"
        v-model:value="day"
        v-decorator="[
          'day',
          {
            rules: [
              {
                required: true,
                message: 'This field is required',
              },
              {
                pattern: /^(0?[1-9]|1\d|2[0-9]|30|31)$/,
                message: 'Invalid value',
              },
            ],
          },
        ]"
        class="form__input"
      >
      </a-input>
    </a-form-item>
    <a-form-item label="MONTH" :colon="false" class="form__item">
      <a-input
        v-model:value="month"
        placeholder="MM"
        v-decorator="[
          'month',
          {
            rules: [
              { required: true, message: 'This field is required' },
              {
                pattern: /^(0?[1-9]|1[0-2])$/,
                message: 'Invalid value',
              },
            ],
          },
        ]"
        class="form__input"
      >
      </a-input>
    </a-form-item>
    <a-form-item label="YEAR" :colon="false" class="form__item">
      <a-input
        v-model:value="year"
        placeholder="YYYY"
        v-decorator="[
          'year',
          {
            rules: [
              { required: true, message: 'This field is required' },
              { min: 4 },
              { max: 4 },
            ],
          },
        ]"
        class="form__input"
      >
      </a-input>
    </a-form-item>
    <a-form-item class="form__arrow">
      <a-button html-type="submit" class="form__button">
        <img
          src="./../assets/icon-arrow.svg"
          class="form__image w-7 h-7"
          alt="arrow-icon"
        />
      </a-button>
    </a-form-item>
  </a-form>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "Form",
  setup() {
    const day = ref(null);
    const month = ref(null);
    const year = ref(null);

    return { day, month, year };
  },
});
</script>

<style lang="scss" scoped>
.form {
  margin-bottom: 1rem;
  padding-bottom: 1.25rem;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  gap: 2rem;
  border-bottom-width: 2px;
  border-bottom-color: #d3d3d3;
}

.form__item {
  display: flex;
  flex-direction: column;
  font-size: 10px;
  letter-spacing: 0.05em;
  font-weight: bold;
  margin-bottom: 0.5rem;
  text-align: start;
  color: #656565;
}

.form__input {
  background-color: transparent;
  color: #333333;
  font-weight: bold;
  font-size: 1.125rem;
  border: 1px solid #d3d3d3;
  border-radius: 0.25rem;
  width: 100%;
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
  padding-left: 0.75rem;
  padding-right: 0.75rem;
  outline: none;
  &::placeholder {
    color: #656565;
    font-weight: bold;
  }

  &:focus {
    border-color: #6b46c1;
  }
}

.form__arrow {
  /* display: inline-flex;
  align-items: center;
  justify-content: flex-end; */
  /* width: 100%; */
}

.form__button {
  position: absolute;
  left: 100px;
  padding: 1rem;
  margin-top: -0.5rem;
  margin-left: -3.5rem;
  border-radius: 50%;
  font-weight: 500;
  color: #333333;
  background-color: #6b46c1;
  cursor: pointer;

  &:hover {
    background-color: #333333;
  }
}

.form__image {
  width: 1.75rem;
  height: 1.75rem;
}
</style>
  