<template>
  <div class="output">
    <div class="date-text">
      <p>
        <span class="date-number">{{
          checkValidity(result) ? result.year : "--"
        }}</span>
        years
      </p>
    </div>
    <div class="date-text">
      <p>
        <span class="date-number">{{
          checkValidity(result) ? result.month : "--"
        }}</span>
        months
      </p>
    </div>
    <div class="date-text">
      <p>
        <span class="date-number">{{
          checkValidity(result) ? result.day : "--"
        }}</span>
        days
      </p>
    </div>
  </div>
</template>

<script setup>
defineProps(["result"]);

const checkValidity = (item) => {
  if (item === null) {
    return false;
  }
  if (item && item.day == NaN) {
    return false;
  } else if (item) {
    return true;
  } else {
    return false;
  }
};
</script>

<style scoped>
.output {
  display: flex;
  flex-direction: column;
  grid-row: 2 / 3;
  border-top: 1px solid var(--light-grey);
  margin-top: 35px;
  padding-top: 10px;
}
@media (max-width: 768px) {
  .output {
    justify-content: center;
  }
}

.date-text {
  font-weight: 800;
  font-style: italic;
}
.date-number {
  color: var(--purple);
}
p {
  font-size: 5rem;
  margin: 0;
}
@media (max-width: 768px) {
  div {
    margin-bottom: -30px;
  }
  p {
    font-size: 4rem;
  }
}
@media (max-width: 480px) {
  div {
    margin-bottom: 0;
  }
  p {
    font-size: 3rem;
  }
}
</style>