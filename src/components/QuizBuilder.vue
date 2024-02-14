<!-- components/QuizBuilder.vue -->
<template>
    <div>
      <h2>Quiz Builder</h2>
      <QuestionComponent
        v-for="(question, index) in questions"
        :key="index"
        :question="question"
        :questionIndex="index"
        @optionSelected="handleOptionSelected"
        @optionsSelected="handleOptionsSelected"
        @answerSubmitted="handleAnswerSubmitted"
        @answersSubmitted="handleAnswersSubmitted"
      />
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  import QuestionComponent from './QuestionComponent.vue';
  
  
  export default {
    components: {
     QuestionComponent,
    },
    data() {
      return {
        questions: ref([
          {
            text: 'What is your favorite programming language?',
            type: 'single-choice',
            options: ['JavaScript', 'Python', 'Java', 'C++'],
          },
          {
            text: 'Which frameworks have you used?',
            type: 'multiple-choice',
            options: ['Vue.js', 'React', 'Angular', 'Express'],
          },
          {
            text: 'Which of the following methods is used to access HTML elements using Javascript?',
            type: 'single-choice',
            options: ['getElementById()', 'getElementByClassName', 'Both A and B', 'None Of The Above'],

          },
          { 
            text: 'Which of the following methods can be used to display data in some form using Javascript?',
            type:  'single-choice',
            options: ['document.write()','console.log()','window.alert()','All Of The Above']
          },
          {
            text: 'What keyword is used to check whether a given property is valid or not?',
            type: 'single-choice',
            options: ['in','is in','lies','exits'],
          }
          // Add more questions as needed
        ]),
      };
    },
    methods: {
      handleOptionSelected(option, questionIndex) {
        console.log(`Selected option for question ${questionIndex + 1}: ${option}`);
        // Handle selected option for single-choice question
      },
      handleOptionsSelected(options, questionIndex) {
        console.log(`Selected options for question ${questionIndex + 1}: ${options}`);
        // Handle selected options for multiple-choice question
      },
      handleAnswerSubmitted(answer, questionIndex) {
        console.log(`Submitted answer for question ${questionIndex + 1}: ${answer}`);
        // Handle submitted answer for single-choice question
      },
      handleAnswersSubmitted(answers, questionIndex) {
        console.log(`Submitted answers for question ${questionIndex + 1}: ${answers}`);
        // Handle submitted answers for multiple-choice question
      },
    },
  };
  </script>
  