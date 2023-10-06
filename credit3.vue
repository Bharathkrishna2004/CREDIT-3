<template>
  <div>
    <p>a. Text Interpolation: {{ message }}</p>
    <p>b. Raw HTML: <span v-html="rawHtml"></span></p>
    <p>c. Attribute Bindings: <div :id="dynamicId"></div></p>
    <p>d. JavaScript expressions inside syntax: {{ 2 + 3 }}</p>

    <button @click="sayHello">Say Hello</button>

    <p>Reactivity Fundamentals: {{ count }}</p>

    <p>Computed Property: {{ computedValue }}</p>

    <div :class="classObject" :style="styleObject">Class and Style Bindings</div>

    <ul>
      <li v-for="item in items" :key="item.id">{{ item.text }}</li>
    </ul>

    <button @click="handleClick">Click me</button>

    <input type="text" v-model="inputValue" />
    <input type="checkbox" v-model="isChecked" />
    <input type="radio" v-model="selectedOption" value="option1" />
    <input type="radio" v-model="selectedOption" value="option2" />
    <select v-model="selectedValue">
      <option value="value1">Option 1</option>
      <option value="value2">Option 2</option>
    </select>
    <textarea v-model="textareaValue"></textarea>

    <p>Watcher: {{ watchedValue }}</p>

    <custom-component :propData="message" @customEvent="handleCustomEvent">
      <template #slotName="slotProps">
        Slot Content: {{ slotProps.slotValue }}
      </template>
    </custom-component>

    <router-link to="/route">Go to Route</router-link>
    <router-view></router-view>
  </div>
</template>

<script>
import { ref, computed } from 'vue';

export default {
  data() {
    return {
      message: "Hello, Vue!",
      rawHtml: "<span style='color: red;'>This is raw HTML</span>",
      dynamicId: "dynamic-element",
      count: ref(0),
      computedValue: computed(() => this.count.value * 2),
      classObject: {
        active: true,
        'text-danger': false,
      },
      styleObject: {
        color: 'blue',
        fontSize: '16px',
      },
      items: [
        { id: 1, text: 'Item 1' },
        { id: 2, text: 'Item 2' },
        { id: 3, text: 'Item 3' },
      ],
      inputValue: '',
      isChecked: false,
      selectedOption: 'option1',
      selectedValue: 'value1',
      textareaValue: '',
      watchedValue: 'initial value',
    };
  },
  methods: {
    sayHello() {
      alert('Hello!');
    },
    handleClick() {
      this.count.value++;
    },
    handleCustomEvent(data) {
      console.log('Custom Event:', data);
    },
  },
};
</script>

<style>
p, button, li, input, select, textarea {
  font-size: 18px;
  margin-bottom: 10px;
}

span {
  color: red;
}

button {
  background-color: #007bff;
  color: #fff;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}

.active {
  background-color: #4caf50;
  color: #fff;
}

li {
  list-style-type: none;
  padding: 5px 0;
}
</style>
