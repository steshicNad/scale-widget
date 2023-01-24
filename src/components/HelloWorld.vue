<template>
  <div class="flex flex-col w-[6.2vw] h-[79.1vh] bg-[#272933]">
    <div
      class="flex items-center w-[1.4vw] h-[2.12vh] ml-[0.31vw] mt-[5vh] text-[#33C300] font-myfont1 font-[600] text-[1.85vh]">
      ДТ
    </div>
    <div class="flex h-[64.27vh] mt-[1.48vh]">
      <!-- main part - 3 столбца еще будет -->
      <div
        class="flex flex-col items-center justify-end gap-[0.56vh] mt-[0.28vh] h-[64.27vh] w-[2.03vw] rounded-[2.6vh] border-4 border-[#3E404C]">
        <div
          class="flex items-center h-[1.57vh] mt-[1.1vh] text-[#33C300] font-myfont1 font-[600] text-[1.57vh]">
          100
        </div>
        <div
          class="flex w-[0.36vw] mb-[1.1vh] bg-[#33C300] rounded-[2.6vh]"
          :style="{ height: parameterHeight() + 'vh' }">
          <!-- тут зеленая палка -->
        </div>
      </div>

      <div class="ml-[0.41vw] mt-[3.69vh]">
        <img src="src/img/scale.svg" class="h-[59.17vh]" />
      </div>

      <div class="flex flex-col items-center gap-[10.56vh] mt-[3.06vh] h-[60.46vh] w-[1vw]">
        <div
          v-for="item in arrayDivisions"
          :key="item"
          class="flex items-center h-[1.29vh] ml-[0.41vw] text-[#D6EBFF] font-myfont1 font-[400] text-[1.1vh]">
          {{ item }}
        </div>
      </div>
    </div>
    <div class="flex flex-col h-[4vh] mt-[3.6vh]">
      <div
        class="flex items-center h-[1.3vh] w-[2.9vw] text-[#D6EBFF] font-myfont1 font-[400] text-[1.1vh]">
        Запас ДТ
      </div>
      <div class="flex h-[2.7vh] text-[#48A7FF] text-[2.2vh]">
        <div class="flex items-center truncate w-[2.9vw] font-myfont1 font-[600]">40.5</div>
        <div class="flex mb-0 items-center truncate font-myfont1 font-[600]">Т</div>
      </div>
    </div>
  </div>
</template>

<script setup>
  import { ref } from 'vue';
  defineProps({
    msg: {
      type: String,
      required: true,
    },
  });

  const arrayDivisions = ref([]);
  const divisionSize = ref(20);
  const startValue = ref(0);
  const divisionsCount = 6;

  const incomingValue = 80;

  for (let index = 0; index < divisionsCount; index++) {
    arrayDivisions.value.push(startValue.value + divisionSize.value * index);
  }
  arrayDivisions.value = arrayDivisions.value.reverse();
  console.log(arrayDivisions.value);

  function parameterHeight() {
    const fullScaleParameterHeight = 59.17;
    const upperLimit = startValue.value + divisionSize.value * 5;
    return (incomingValue * fullScaleParameterHeight) / upperLimit;
  }

  const stateHeight = ref({
    height: '100vh',
  });
</script>
