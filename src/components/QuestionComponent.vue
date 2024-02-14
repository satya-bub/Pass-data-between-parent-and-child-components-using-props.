<!-- components/QuestionComponent.vue -->
<template>
  <div>
    <h3 v-if="question && question.text">{{ question.text }}</h3>
    <div v-if="question && question.type === 'single-choice'">
      <label v-for="(option, index) in question.options" :key="index">
        <input
          type="radio"
          :name="`question-${questionIndex}`"
          :value="option"
          :checked="selectedOptions.includes(option)"
          @change="handleOptionSelected(option)"
        />
        {{ option }}
      </label>
    </div>
    <div v-if="question && question.type === 'multiple-choice'">
      <label v-for="(option, index) in question.options" :key="index">
        <input
          type="checkbox"
          :value="option"
          :checked="selectedOptions.includes(option)"
          @change="handleOptionSelected(option)"
        />
        {{ option }}
      </label>
    </div>
    <button @click="submitAnswer">Submit</button>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  props: {
    question: Object,
    questionIndex: Number,
  },
  setup(props, { emit }) {
    const selectedOptions = ref([]);

    const handleOptionSelected = (option) => {
      const index = selectedOptions.value.indexOf(option);
      if (index === -1) {
        selectedOptions.value.push(option);
      } else {
        selectedOptions.value.splice(index, 1);
      }
    };

    const submitAnswer = () => {
      if(selectedOptions.value.length === 0){
      alert('please select any option ! before submit')}
      else{
      if (props.question && props.question.type === 'single-choice') {
        emit('optionsSelected', selectedOptions.value, props.questionIndex);
      } else if (props.question && props.question.type === 'multiple-choice') {
        emit('optionsSelected', selectedOptions.value, props.questionIndex);
      }
    }
    };

    return {
      selectedOptions,
      handleOptionSelected,
      submitAnswer,
    };
  },
};
</script>
<style scoped>
  /* Container styles */
  div {
    margin-bottom: 20px;
  }

  /* Question text styles */
  h3 {
    font-size: 18px;
    margin-bottom: 10px;
  }

  /* Option label styles */
  label {
    display: block;
    margin-bottom: 8px;
    cursor: pointer;
  }

  /* Radio and checkbox styles */
  input[type="radio"],
  input[type="checkbox"] {
    margin-right: 8px;
  }

  /* Button styles */
  button {
    padding: 10px 15px;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  /* Button hover effect */
  button:hover {
    background-color: #45a049;
  }
</style>
