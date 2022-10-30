//获取试卷并跳转到添加题库
<template>
  <div class="exam">
    <el-table :data="tableData" border>
      <el-table-column fixed="left" prop="source" label="试卷名称" width="180"></el-table-column>
      <el-table-column prop="description" label="介绍" width="200"></el-table-column>
      <el-table-column prop="institute" label="所属学院" width="120"></el-table-column>
      <el-table-column prop="major" label="所属专业" width="200"></el-table-column>
      <el-table-column prop="grade" label="年级" width="100"></el-table-column>
      <el-table-column prop="examDate" label="考试日期" width="120"></el-table-column>
      <el-table-column prop="totalTime" label="持续时间" width="120"></el-table-column>
      <el-table-column prop="totalScore" label="总分" width="120"></el-table-column>
      <el-table-column prop="type" label="试卷类型" width="120"></el-table-column>
      <el-table-column prop="tips" label="考生提示" width="400"></el-table-column>
      <el-table-column fixed="right" label="操作" width="150">
        <template slot-scope="scope">
          <el-button @click="add()" type="primary" size="small">增加题库</el-button>
        </template>
      </el-table-column>
    </el-table>
    <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :current-page="pagination.current"
      :page-sizes="[4, 8, 10, 20]"
      :page-size="pagination.size"
      layout="total, sizes, prev, pager, next, jumper"
      :total="pagination.total" class="page">
    </el-pagination>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {}, //保存点击以后当前试卷的信息
      pagination: { //分页后的考试信息
        current: 1, //当前页
        total: null, //记录条数
        size: 4 //每页条数
      },
      tableData: [{
        source: '基础要素能力测试',
        description: '基础要素能力测试',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'面试基础',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '面试细节测试与训练',
        description: '面试细节测试与训练',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'面试基础',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '听题能力测试与训练',
        description: '听题能力测试与训练',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'面试基础',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '思考习惯测试与训练',
        description: '思考习惯测试与训练',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'面试基础',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '语言能力和技巧测试与训练',
        description: '语言能力和技巧测试与训练',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'面试基础',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '答题声音检测',
        description: '答题声音检测',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'面试基础',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '基础要素能力测试',
        description: '人机测试与训练，专家测试与训练，测试过程监测与行为分析，测试结果分析与展示',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'结构化面试',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '综合分析能力测试与训练',
        description: '人机测试与训练，模拟测试与训练，专家测试与训练',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'结构化面试',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '计划组织协调能力测试与训练',
        description: '人机测试与训练，拟测试与训练，专家测试与训练',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'结构化面试',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '解决实际问题能力测试与训练',
        description: '人机测试与训练，拟测试与训练，专家测试与训练',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'结构化面试',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '应变能力测试与训练',
        description: '人机测试与训练，拟测试与训练，专家测试与训练',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'结构化面试',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '人际沟通能力测试与训练',
        description: '人机测试与训练，拟测试与训练，专家测试与训练',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'结构化面试',
        tips:'今日不努力，明日做苦力'
      }, {
        source: '模拟测试',
        description: '线上模拟测试，线下模拟测试，模拟测试与训练，测试结果与打分情况展示，专家点评',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'结构化面试',
        tips:'今日不努力，明日做苦力'
      },{
        source: '基础要素能力测试',
        description: '人机测试与训练，专家测试与训练，测试过程监测与行为分析，测试结果分析与展示',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'无领导小组讨论',
        tips:'今日不努力，明日做苦力'
      },{
        source: '模拟测试',
        description: '线上模拟测试，线下模拟测试，模拟测试与训练，测试结果与打分情况展示，专家点评',
        institute: '无限制',
        major:'无限制',
        grade:'无限制',
        examDate:'2022-10-06',
        totalTime:'20',
        totalScore:'100',
        type:'无领导小组讨论',
        tips:'今日不努力，明日做苦力'
      }],
    }
  },
  created() {
    this.getExamInfo()
  },
  methods: {
    getExamInfo() { //分页查询所有试卷信息
      this.$axios(`/api/exams/${this.pagination.current}/${this.pagination.size}`).then(res => {
        this.pagination = res.data.data
      }).catch(error => {
      })
    },
    //改变当前记录条数
    handleSizeChange(val) {
      this.pagination.size = val
      this.getExamInfo()
    },
    //改变当前页码，重新发送请求
    handleCurrentChange(val) {
      this.pagination.current = val
      this.getExamInfo()
    },
    add() { //增加题库
      this.$router.push({path:'/addInterviewChildren'})
    }
  },
};
</script>
<style lang="scss" scoped>
.exam {
  padding: 0px 40px;
  .page {
    margin-top: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .edit{
    margin-left: 20px;
  }
}
</style>
