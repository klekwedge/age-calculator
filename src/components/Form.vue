<template>
  <a-form
    class="mb-4 pb-5 flex flex-col md:flex-row justify-start gap-8 border-b-2 border-light-gray"
  >
    <a-form-item
      label="DAY"
      :colon="false"
      class="block text-smokey-grey text-[10px] tracking-widest font-bold mb-2 text-start"
    >
      <a-input
        placeholder="DD"
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
        class="bg-transparent text-off-black font-bold text-lg border border-light-gray rounded md:w-28 w-full py-2 px-3 focus:outline-none placeholder:text-smokey-grey placeholder:font-extrabold uppercase focus:border-off-purple"
      >
      </a-input>
    </a-form-item>
    <a-form-item
      label="MONTH"
      :colon="false"
      class="block text-smokey-grey text-[10px] tracking-widest font-bold mb-2 text-start"
    >
      <a-input
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
        class="bg-transparent text-off-black font-bold text-lg border border-light-gray rounded md:w-28 w-full py-2 px-3 focus:outline-none placeholder:text-smokey-grey placeholder:font-extrabold uppercase focus:border-off-purple"
      >
      </a-input>
    </a-form-item>
    <a-form-item
      label="YEAR"
      :colon="false"
      class="block text-smokey-grey text-[10px] tracking-widest font-bold mb-2 text-start"
    >
      <a-input
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
        class="bg-transparent text-off-black font-bold text-lg border border-light-gray rounded md:w-28 w-full py-2 px-3 focus:outline-none placeholder:text-smokey-grey placeholder:font-extrabold uppercase focus:border-off-purple"
      >
      </a-input>
    </a-form-item>
    <a-form-item class="inline-flex items-center justify-end w-full">
      <a-button
        html-type="submit"
        class="absolute p-4 md:mt-6 -mt-2 -ml-14 rounded-full font-medium text-gray-900 bg-off-purple hover:bg-off-black hover:cursor-pointer"
      >
        <img
          src="./assets/images/icon-arrow.svg"
          class="w-7 h-7"
          alt="arrow-icon"
        />
      </a-button>
    </a-form-item>
  </a-form>
</template>
  
<script lang="ts">
export default {
  name: "Form",
  setup() {
    return {};
  },
};
</script>
  
  <style scoped>
</style>
  