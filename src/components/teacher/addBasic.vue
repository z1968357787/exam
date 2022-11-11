//获取试卷并跳转到添加题库
<template>
  <div class="exam">
    <el-table :data="tableData" border>
      <el-table-column fixed="left" prop="source" label="模块名称" width="350"></el-table-column>
      <el-table-column prop="description" label="模块介绍" width="600"></el-table-column>
      <el-table-column fixed="right" label="操作" width="150">
        <template slot-scope="scope">
          <el-button @click="add(scope.row.source)" type="primary" size="small">添加内容</el-button>
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
        source: '好文章读背、赏析与分享',
        description: '可以导入专家指定文章，也可以由用户推荐，但要提出推荐理由，并经专家审核导入',
      }, {
        source: '名人名句读背、赏析与分享',
        description: '可以导入专家指定名人名句，也可以由用户推荐，但要提出推荐理由，并经专家审核导入',
      }, {
        source: '焦点和热点新闻社评、社论读背、赏析与分享',
        description: '只能选定人民网或者新华网的焦点和热点新闻社评、社论读背、赏析与分享',
      }, {
        source: '思维方法学习、复习',
        description: '可以导入专家指定关于思维方法文章，也可以由用户推荐，但要提出推荐理由',
      }, {
        source: '学习成果测试',
        description: '每天上午下午测试相同的内容，进行周排名和月度排名，一次全部答对的可以主动分享',
      }, {
        source: '线上视频辅导和答疑',
        description: '可以一对多，一对一，用户也可以预设问题，专家选附议多的问题优先辅导并发布辅导预告',
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
