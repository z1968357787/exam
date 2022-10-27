// 我的考试页面
<template>
  <div id="myExam">
    <div class="title">面试训练</div>
    <div class="wrapper">
      <ul class="top">
        <li class="order" >
          <a @click="exam(1)">
           <el-badge :value="12" class="item" type="primary">
             <span>面试基础能力</span>
           </el-badge>
          </a>
        </li>
        <li class="order">
          <a @click="exam(2)">
           <el-badge :value="1" class="item" type="primary">
             <span>结构化面试</span>
           </el-badge>
          </a>
        </li>
        <li class="order">
          <a @click="exam(3)">
           <el-badge :value="2" class="item" type="primary">
            <span>无领导小组讨论</span>
           </el-badge>
          </a>
        </li>
        <!--<li class="order">
          <el-badge :value="1" class="item">
            <span>已过期</span>
          </el-badge>
        </li>-->
        <li class="search-li"><div class="icon"><input type="text" placeholder="试卷名称" class="search" v-model="key"><i class="el-icon-search"></i></div></li>
        <li><el-button type="primary" @click="search()">搜索试卷</el-button></li>
      </ul>
      <ul class="paper" v-loading="loading" v-if="examState==1">
        <li class="item">
          <h4 @click="toExamMsg(examState)">基础要素能力测试</h4>
          <p class="name">基础要素能力测试</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">面试细节测试与训练</h4>
          <p class="name">面试细节测试与训练</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">听题能力测试与训练</h4>
          <p class="name">听题能力测试与训练</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">思考习惯测试与训练</h4>
          <p class="name">思考习惯测试与训练</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">语言能力和技巧测试与训练</h4>
          <p class="name">语言能力和技巧测试与训练</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">答题声音检测</h4>
          <p class="name">答题声音检测</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
      </ul>

      <ul class="paper" v-loading="loading" v-if="examState==2">
        <li class="item">
          <h4 @click="toExamMsg(examState)">基础要素能力测试</h4>
          <p class="name">人机测试与训练，专家测试与训练，测试过程监测与行为分析，测试结果分析与展示</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">综合分析能力测试与训练</h4>
          <p class="name">人机测试与训练，模拟测试与训练，专家测试与训练</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">计划组织协调能力测试与训练</h4>
          <p class="name">人机测试与训练，拟测试与训练，专家测试与训练</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">解决实际问题能力测试与训练</h4>
          <p class="name">人机测试与训练，模拟测试与训练，专家测试与训练</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">应变能力测试与训练</h4>
          <p class="name">人机测试与训练，模拟测试与训练，专家测试与训练</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">人际沟通能力测试与训练</h4>
          <p class="name">人机测试与训练，模拟测试与训练，专家测试与训练</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">模拟测试</h4>
          <p class="name">线上模拟测试，线下模拟测试，模拟测试与训练，测试结果与打分情况展示，专家点评</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
      </ul>

      <ul class="paper" v-loading="loading" v-if="examState==3">
        <li class="item">
          <h4 @click="toExamMsg(examState)">基础要素能力测试</h4>
          <p class="name">人机测试与训练，专家测试与训练。测试过程监测与行为分析，测试结果分析与展示</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
        <li class="item">
          <h4 @click="toExamMsg(examState)">模拟测试</h4>
          <p class="name">线上模拟测试，线下模拟测试，模拟测试与训练，测试结果与打分情况展示，专家点评</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>2022-10-06</span>
            <i class="iconfont icon-icon-time"></i><span>限时20分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分100分</span>
          </div>
        </li>
      </ul>

      <div class="pagination">
        <el-pagination
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
          :current-page="pagination.current"
          :page-sizes="[6, 10, 20, 40]"
          :page-size="pagination.size"
          layout="total, sizes, prev, pager, next, jumper"
          :total="pagination.total">
        </el-pagination>
      </div>
    </div>
  </div>
</template>

<script>
import {mapState} from "vuex";

export default {
  // name: 'myExam'
  data() {
    return {
      loading: false,
      key: null, //搜索关键字
      allExam: null, //所有考试信息
      examState: 1,
      pagination: { //分页后的考试信息
        current: 1, //当前页
        total: null, //记录条数
        size: 6 //每页条数
      }
    }
  },
  created() {
    this.getExamInfo()
    this.loading = true
  },
  // watch: {

  // },
  methods: {
    //获取当前所有考试信息
    getExamInfo() {
      this.$axios(`/api/exams/${this.pagination.current}/${this.pagination.size}`).then(res => {
        this.pagination = res.data.data
        this.loading = false
        console.log(this.pagination)
      }).catch(error => {
        console.log(error)
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
    //搜索试卷
    search() {
      this.$axios('/api/exams').then(res => {
        if(res.data.code == 200) {
          let allExam = res.data.data
          let newPage = allExam.filter(item => {
            return item.source.includes(this.key)
          })
          this.pagination.records = newPage
        }
      })
    },
    //跳转到试卷详情页
    toExamMsg(examState) {
      this.$router.push({path: '/interviewMsg', query: {examCode: 20190001,examState:examState}})
      console.log(examState)
    },
    exam(examState) { //跳转考试模式
      this.$data.examState=examState;
    }
  }
}
</script>


<style lang="scss" scoped>
.pagination {
  padding: 20px 0px 30px 0px;
  .el-pagination {
    display: flex;
    justify-content: center;
  }
}
.paper {
  h4 {
    cursor: pointer;
  }
}
.paper .item a {
  color: #000;
}
.wrapper .top .order {
  cursor: pointer;
}
.wrapper .top .order:hover {
  color: #0195ff;
  border-bottom: 2px solid #0195ff;
}
.wrapper .top .order:visited {
  color: #0195ff;
  border-bottom: 2px solid #0195ff;
}
.item .info i {
  margin-right: 5px;
  color: #0195ff;
}
.item .info span {
  margin-right: 14px;
}
.paper .item {
  width: 380px;
  border-radius: 4px;
  padding: 20px 30px;
  border: 1px solid #eee;
  box-shadow: 0 0 4px 2px rgba(217,222,234,0.3);
  transition: all 0.6s ease;
}
.paper .item:hover {
  box-shadow: 0 0 4px 2px rgba(140, 193, 248, 0.45);
  transform: scale(1.03);
}
.paper .item .info {
  font-size: 14px;
  color: #88949b;
}
.paper .item .name {
  font-size: 14px;
  color: #88949b;
}
.paper * {
  margin: 20px 0;
}
.wrapper .paper {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.top .el-icon-search {
  position: absolute;
  right: 10px;
  top: 10px;
}
.top .icon {
  position: relative;
}
.wrapper .top {
  border-bottom: 1px solid #eee;
  margin-bottom: 20px;
}
#myExam .search-li {
  margin-left: auto;
}
.top .search-li {
  margin-left: auto;
}
.top li {
  display: flex;
  align-items: center;
}
.top .search {
  margin-left: auto;
  padding: 10px;
  border-radius: 4px;
  border: 1px solid #eee;
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075);
  transition: border-color ease-in-out .15s,box-shadow ease-in-out .15s;
}
.top .search:hover {
  color: #0195ff;
  border-color: #0195ff;
}
.wrapper .top {
  display: flex;
}
.wrapper .top li {
  margin: 20px;
}
#myExam {
  width: 980px;
  margin: 0 auto;
}
#myExam .title {
  margin: 20px;
}
#myExam .wrapper {
  background-color: #fff;
}
.wrapper .top .order {
  cursor: pointer;
}
.wrapper .top .order:hover {
  color: #0195ff;
  border-bottom: 2px solid #0195ff;
}
.wrapper .top .order:visited {
  color: #0195ff;
  border-bottom: 2px solid #0195ff;
}
.item .info i {
  margin-right: 5px;
  color: #0195ff;
}
.item .info span {
  margin-right: 14px;
}
.paper .item {
  border-radius: 4px;
  padding: 20px 30px;
  border: 1px solid #eee;
  box-shadow: 0 0 4px 2px rgba(217,222,234,0.3);
  transition: all 0.6s ease;
}
.paper .item:hover {
  box-shadow: 0 0 4px 2px rgba(140, 193, 248, 0.45)
}
.paper .item .info {
  font-size: 14px;
  color: #88949b;
}
.paper .item .name {
  font-size: 14px;
  color: #88949b;
}
.paper * {
  margin: 20px 0;
}
.wrapper .paper {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
.top .el-icon-search {
  position: absolute;
  right: 10px;
  top: 10px;
}
.top .icon {
  position: relative;
}
.wrapper .top {
  border-bottom: 1px solid #eee;
}
#myExam .search-li {
  margin-left: auto;
}
.top .search-li {
  margin-left: auto;
}
.top li {
  display: flex;
  align-items: center;
}
.top .search {
  margin-left: auto;
  padding: 10px;
  border-radius: 4px;
  border: 1px solid #eee;
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075);
  transition: border-color ease-in-out .15s,box-shadow ease-in-out .15s;
}
.top .search:hover {
  color: #0195ff;
  border-color: #0195ff;
}
.wrapper .top {
  display: flex;
}
.wrapper .top li {
  margin: 20px;
}
#myExam {
  width: 980px;
  margin: 0 auto;
}
#myExam .title {
  margin: 20px;
}
#myExam .wrapper {
  background-color: #fff;
}
</style>
