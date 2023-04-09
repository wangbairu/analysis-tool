<template>
    <div class="head">
        <el-button @click="addInput" type="primary">添加维度</el-button>
        <el-button @click="generate" type="primary">生成</el-button>
        <el-form :model="formData" ref="form" class="shape-class">
            <el-form-item v-for="(demention, index) in shape" :key="index" :label="'Input ' + (index + 1)">
                <el-input-number v-model="demention.value" :min="0" :step="1" controls-position="right"></el-input-number>
                <el-button @click="removeInput(index)">删除</el-button>
            </el-form-item>
        </el-form>
    </div>
    <div v-for="i in shape[shape.length - 2]?.value" :key="i">
        <div class="grid">
            <div v-for="i in shape[shape.length - 1]?.value" :key="i" class="grid-item" :style="gridItem()">
                {{ i }}
            </div>
        </div>
    </div>
</template>
  
<script setup>
import { ref } from 'vue';
const shape = ref([]);

const addInput = () => {
    shape.value.push({ value: 0 });
};

const removeInput = (index) => {
    shape.value.splice(index, 1);
};
const gridItem = () => {
    // return `width: calc(100% /${shape.value[shape.value.length - 1].value} - 4px);
    //         height: calc(100% /${shape.value[shape.value.length - 1].value} - 4px);
    //         `
    return `width: calc(500px/${shape.value[shape.value.length - 1].value} - 4px);
            height: calc(500px/${shape.value[shape.value.length - 1].value} - 4px);
            `
}
const generate = () => {
    console.log(shape.value[shape.value.length - 1].value)
}

const formData = ref({});

</script>

<style scoped lang="less">
.head {
    .shape-class {
        width: 300px;
        max-height: 200px;
        overflow-y: auto;
    }
}
.grid {
  display: flex;
  flex-wrap: wrap;
  background-color: red;

  .grid-item {
    cursor: pointer;
    margin: 2px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #eee;
  }
  .grid-item:hover {
    transform: scale(1.2);
  }
}

</style>
  