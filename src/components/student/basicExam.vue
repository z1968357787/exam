// 我的考试页面
<template>
  <div id="myExam">
    <div class="title">基础模块</div>
    <div class="wrapper">
      <ul class="top">
        <li class="order" >
          <a @click="exam(1)">
           <el-badge :value="12" class="item" type="primary">
             <span>文章读背</span>
           </el-badge>
          </a>
        </li>
        <li class="order">
          <a @click="exam(2)">
           <el-badge :value="1" class="item" type="primary">
             <span>名人名句</span>
           </el-badge>
          </a>
        </li>
        <li class="order">
          <a @click="exam(3)">
           <el-badge :value="2" class="item" type="primary">
             <span>时事评论</span>
           </el-badge>
          </a>
        </li>
        <li class="order">
          <a @click="exam(4)">
           <el-badge :value="1" class="item" type="primary">
             <span>思维方法</span>
           </el-badge>
          </a>
        </li>
        <li class="order">
          <a @click="exam(5)">
           <el-badge :value="1" class="item" type="primary">
             <span>成果测试</span>
           </el-badge>
          </a>
        </li>
        <li class="order">
          <a @click="exam(6)">
           <el-badge :value="1" class="item" type="primary">
             <span>视频答疑</span>
           </el-badge>
          </a>
        </li>

        <li class="search-li"><div class="icon"><input type="text" placeholder="内容名称" class="search" v-model="key"><i class="el-icon-search"></i></div></li>
        <li><el-button type="primary" @click="search()">搜索内容</el-button></li>
      </ul>
      <ul class="paper" v-loading="loading" v-if="examState==1">
        <li class="item" v-for="(item,index) in pagination.records" :key="index">
          <h4 @click="toContentMsg(item.examCode,examState)">我们为什么需要良好的家风</h4>
          <p class="name">心口如一，童臾无欺</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>{{item.examDate.substr(0,10)}}</span>
            <i class="iconfont icon-icon-time"></i><span v-if="item.totalTime != null">浏览次数 132次</span>
            <i class="iconfont icon-fenshu"></i><span>发布人 周治平</span>
          </div>
        </li>
      </ul>
      <ul class="paper" v-loading="loading" v-if="examState==2">
        <li class="item" v-for="(item,index) in pagination.records" :key="index">
          <h4 @click="toContentMsg(item.examCode,examState)">与肝胆人共事，无字句处读书</h4>
          <p class="name">周恩来</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>{{item.examDate.substr(0,10)}}</span>
            <i class="iconfont icon-icon-time"></i><span v-if="item.totalTime != null">浏览次数 591次</span>
            <i class="iconfont icon-fenshu"></i><span>发布人 谭嘉展</span>
          </div>
        </li>
      </ul>
      <ul class="paper" v-loading="loading" v-if="examState==3">
        <li class="item" v-for="(item,index) in pagination.records" :key="index">
          <h4 @click="toContentMsg(item.examCode,examState)">希腊学者读中共二十大报告: 中国是全人类稳定和发展的因素</h4>
          <p class="name">中央广电总台国际在线</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>{{item.examDate.substr(0,10)}}</span>
            <i class="iconfont icon-icon-time"></i><span v-if="item.totalTime != null">浏览次数 156次</span>
            <i class="iconfont icon-fenshu"></i><span>发布人 王乐</span>
          </div>
        </li>
      </ul>
      <ul class="paper" v-loading="loading" v-if="examState==4">
        <li class="item" v-for="(item,index) in pagination.records" :key="index">
          <h4 @click="toContentMsg(item.examCode,examState)">唯物辩证法</h4>
          <p class="name">辩证唯物主义</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>{{item.examDate.substr(0,10)}}</span>
            <i class="iconfont icon-icon-time"></i><span v-if="item.totalTime != null">浏览次数 265次</span>
            <i class="iconfont icon-fenshu"></i><span>发布人 宋文林</span>
          </div>
        </li>
      </ul>
      <ul class="paper" v-loading="loading" v-if="examState==5">
        <li class="item" v-for="(item,index) in pagination.records" :key="index">
          <h4 @click="toContentMsg(item.examCode,examState)">学习小测</h4>
          <p class="name">不会有人连小测试都过不了吧</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>{{item.examDate.substr(0,10)}}</span>
            <i class="iconfont icon-icon-time"></i><span v-if="item.totalTime != null">限时{{item.totalTime}}分钟</span>
            <i class="iconfont icon-fenshu"></i><span>满分{{item.totalScore}}分</span>
          </div>
        </li>
      </ul>
      <ul class="paper" v-loading="loading" v-if="examState==6">
        <li class="item" v-for="(item,index) in pagination.records" :key="index">
          <h4 @click="toContentMsg(item.examCode,examState)">习题答疑</h4>
          <p class="name">奇怪的知识又变多了呢</p>
          <div class="info">
            <i class="el-icon-loading"></i><span>{{item.examDate.substr(0,10)}}</span>
            <i class="iconfont icon-icon-time"></i><span v-if="item.totalTime != null">浏览次数 278次</span>
            <i class="iconfont icon-fenshu"></i><span>发布人 关锦权</span>
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
    toContentMsg(examCode,examState) {
      this.$router.push({path: '/contentMsg', query: {examCode: examCode,examState:examState}})
      console.log(examCode)
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
