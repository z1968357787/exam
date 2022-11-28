//获取试卷并跳转到添加题库
<template>
  <div class="exam">
    <el-table :data="tableData" border>
      <el-table-column fixed="left" prop="title" label="标题" width="200"></el-table-column>
      <el-table-column prop="source" label="推荐专家" width="200"></el-table-column>
      <el-table-column prop="classification" label="类型" width="200"></el-table-column>
      <el-table-column prop="description" label="内容介绍" width="200"></el-table-column>
      <el-table-column prop="content" label="内容详情" width="200"></el-table-column>
      <el-table-column prop="recommendation" label="推荐理由" width="200"></el-table-column>
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
        title:'雷雨',
        source: '白岩松',
        classification:'好文章读背',
        description: '一篇关于家庭教育的文章',
        content:'此处省略1000字...',
        recommendation:'就是很好'
      }, {
        title:'毛泽东的名言',
        source: '白岩松',
        classification:'名言名句',
        description: '关于毛泽东的名言',
        content:'此处省略1000字...',
        recommendation:'就是很好'
      }, {
        title:'足球的魅力，就是一切皆有可能',
        source: '白岩松',
        classification:'时事评论',
        description: '一篇时事评论',
        content:'此处省略1000字...',
        recommendation:'就是很好'
      }, {
        title:'马克思主义哲学论',
        source: '白岩松',
        classification:'思维方法',
        description: '一篇关于思维方法的文章',
        content:'此处省略1000字...',
        recommendation:'就是很好'
      }, {
        title:'好题测试',
        source: '白岩松',
        classification:'成果测试',
        description: '学累了，就来测试一下吧',
        content:'此处省略1000字...',
        recommendation:'就是很好'
      }, {
        title:'宋浩精讲',
        source: '白岩松',
        classification:'视频答疑',
        description: '关于申论的解答教学',
        content:'此处省略1000字...',
        recommendation:'就是很好'
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
    add(source) { //增加题库
      if(source=='学习成果测试'){
        this.$router.push({path:'/addAnswerChildren'})
      }else if(source=='线上视频辅导和答疑'){
        this.$router.push({path:'/addInterviewChildren'})
      } else {
        this.$router.push({path:'/addBasicChildren'})
      }

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
