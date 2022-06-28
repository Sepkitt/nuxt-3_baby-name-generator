<script setup lang="ts">
import { Gender, Length, Popularity } from "@/data";

interface OptionProps {
    choice: {
        title: string;
        type:string;
        buttons: Gender[] | Popularity[] | Length[];
    };
    options: {
        gender: Gender;
        popularity: Popularity;
        length: Length;
    };

}

const props = defineProps<OptionProps>();
</script>

<template>
  <div class="option-container" 
           >
 <!-- v-for="(choice, optIndex) in choices" :key="optIndex" -->
        <h4>{{choice.title}}</h4>
        <div class="option-buttons">
          <button class="option"  
          v-for="(button, btnIndex) in choice.buttons" :key="btnIndex"
          :class="[
            {'option-active' : options[choice.type] === button},
            {'option-right' : btnIndex === (choice.buttons.length-1)}, 
            {'option-left' : btnIndex === 0} ]"

          @click="options[choice.type] = button"
          
          >
          {{button}}</button>
          
        </div>
      </div>
</template>



<style scoped>
.option-container {
  margin-bottom: 2rem;
}
.option {
  background: white;
  outline: 0.15rem solid rgb(249, 87, 89);
  border: none;
  padding: 0.75rem;
  width: 12rem;
  font-size: 1rem;
  color: rgb(27, 60, 138);
  cursor: pointer;
  font-weight: 200;
}
.option-left {
  border-radius: 1rem 0 0 1rem;
}
.option-right {
  border-radius: 0 1rem 1rem 0;
}
.option-active {
  background-color: rgb(249, 87, 89);
  color: white;
}
</style>