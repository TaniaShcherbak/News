<template>
    <div>
      <!-- My first component
      {{ test == 42 ? "it is 42" : "not 42" }}
      <p v-bind:class="ClassName">Some text</p>
      <p v-if="test == 43">if work</p>
      <p v-else>else work</p> -->
      {{ post.name }}, {{ post.date }}
      <br />
      {{ testCopy }}
      <br />
      <!-- <div class="pointer" @click="counter++">Click me</div> -->
      <div class="pointer" @click="onClickCounter">Click me</div>
      <p class="border">{{ counter }}</p>
      <div @mouseover="onMouseOver">
        please hover me
        {{ hoverCounter }}
      </div>
  
    </div>
  </template>
  
  <script>
  export default {
    name: "PostComponent",
    props: {
      post: {
        type: Object,
        required: true,
        default: () => {
          return { name: "without number", date: "today" };
        },
      },
      test: {
        type: Number,
      },
      id: {
        type: Number,
      }
    },
    mounted() {
      (this.testCopy = this.test), (this.testCopy = 44);
    },
    data() {
      return {
        testCopy: "",
        ClassName: "my-first-component",
        counter: 0,
        hoverCounter: 0,
      };
    },
    methods: {
      onClickCounter() {
        this.consolog(this.counter);
        this.counter++;
        this.$emit("clickCounter", this.counter, this.id)
      },
      consolog(number) {
        console.log(number);
      },
      onMouseOver(event) {
        this.hoverCounter++;
        console.log(event);
      },
    },
  };
  </script>
  <style>
  .pointer {
    cursor: pointer;
  }
  
  .border {
    border: 2px solid black;
    width: 50px;
    margin: 0 auto;
  }
  </style>