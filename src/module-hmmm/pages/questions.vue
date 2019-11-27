<template>
  <div class="dashboard-container">
    <div class="app-container">
      <el-card class="box-card">
        <div class="text item">
          <el-row>
            <el-col :span="6">
              <div class="grid-content bg-purple-dark">
                学科: 
                <el-select v-model="searchForm.subjectID" placeholder="请选择">
                  <el-option v-for="item in subjectIDList" :key="item.value" :label="item.label" :value="item.value"></el-option>
                </el-select>
              </div>
            </el-col>
            <el-col :span="6">
              <div class="grid-content bg-purple-dark">
                难度: 
                <el-select v-model="searchForm.difficulty" placeholder="请选择">
                  <el-option v-for="item in difficultyList" :key="item.value" :label="item.label" :value="item.value"></el-option>
                </el-select>
              </div>
            </el-col>
            <el-col :span="6">
              <div class="grid-content bg-purple-dark">
                试题类型: 
                <el-select v-model="searchForm.questionType" placeholder="请选择">
                  <el-option v-for="item in questionTypeList" :key="item.value" :label="item.label" :value="item.value"></el-option>
                </el-select>
              </div>
            </el-col>
            <el-col :span="6">
              <div class="grid-content bg-purple-dark"></div>
            </el-col>
          </el-row>
        </div>
      </el-card>
    </div>
  </div>
</template>

<script>
import {simple} from '@/api/hmmm/subjects'
import {difficulty as difficultyList, questionType as questionTypeList} from '@/api/hmmm/constants'

export default {
  name: 'QuestionsList',
  created() {
    this.getsubjectIDList()
  },
  data() {
    return {
      subjectIDList: [],
      difficultyList,
      questionTypeList,
      searchForm: {
        subjectID: '',
        difficulty: '',
        questionType: ''
      }
    }
  },
  methods: {
    async getsubjectIDList() {
      var rst = await simple()
      console.log(rst)
      this.subjectIDList = rst.data
    },
    async getdifficultyList() {
      var rst = await simple()
      console.log(rst)
      this.difficultyList = rst.data
    }
  }
}
</script>

<style scoped>
.el-select{
  /* width: 80%; */
}
</style>
