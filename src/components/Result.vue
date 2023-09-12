<template>
  <div>
    <ul class="result__list">
      <li class="result__item">
        <!-- <span :class="calculate[item] ? '' : 'tracking-[15px]'">{{ calculate[item] ?? '--'}}</span> -->
        <!-- <span class="result__text">{{item}}</span> -->
      </li>
    </ul>
  </div>
</template>
    
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Result",
  setup() {},
});
</script>
    
<style lang="scss" scoped>
.result__list {
  display: flex;
  flex-direction: column;
}

.result__item {
  font-weight: bold;
  font-size: 6rem;
  font-style: italic;
  color: #6b46c1;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}
.result__text {
  color: #333333;
  font-weight: 900;
  padding-left: 0.25rem;
}
</style>
    