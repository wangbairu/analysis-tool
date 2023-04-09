<template>
    <div>
        <el-button type="primary" @click="addDemension">添加维度</el-button>
        <div v-for="(demension, index) in shape" :key="index">
            <el-input-number :placeholder="'Input ' + (index + 1)" />

            <!-- <input :placeholder="'Input ' + (index + 1)" :value="input" @input="updateInput($event.target.value, index)" /> -->
            <button @click="removeDimension(index)">删除维度</button>
        </div>
    </div>
</template>
  
<script setup>
import { ref } from 'vue';
const shape = ref([]);

const addDemension = () => {
    shape.value.push('');
};

const updateInput = (value, index) => {
    shape.value[index] = value;
};

const removeDimension = (index) => {
    shape.value.splice(index, 1);
};
</script>
  