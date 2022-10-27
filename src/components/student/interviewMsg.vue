// 点击试卷后的缩略信息
<template>
  <div id="msg">

    <div class="title" v-if="examState==1">
      <span >面试模块</span>
      <span>/  面试基础</span>
    </div>
    <div class="wrapper" v-if="examState==1">
      <ul class="top">
        <li class="example">面试基础</li>
        <li><i class="iconfont icon-pen-"></i></li>
        <li><i class="iconfont icon-share"></i></li>
        <li class="right">
          <div>
            <span class="count">总分</span>
            <span class="score">{{score[0]+score[1]+score[2]}}</span>
          </div>
        </li>
      </ul>
      <ul class="bottom">
        <li>更新于{{examData.examDate}}</li>
        <li>来自 {{examData.institute}}</li>
        <li class="btn">{{examData.type}}</li>
        <li class="right"><el-button @click="commit()">完成面试</el-button></li>
      </ul>
      <ul class="info">
        <li @click="dialogVisible = true"><a href="javascript:;"><i class="iconfont icon-info"></i>面试须知</a></li>
      </ul>
    </div>
    <div class="content" v-if="examState==1">
      <el-collapse v-model="activeName" >
        <el-collapse-item class="header" name="0">
          <template slot="title" class="stitle">
            <div class="title">
              <span>面试基础练习</span><i class="header-icon el-icon-info"></i>
              <!--<span class="time">{{examData.totalScore}}分 / {{examData.totalTime}}分钟</span>-->
              <span class="time">100分 / 20分钟</span>
              <el-button type="primary" size="small">点击查看面试详情</el-button>
            </div>
          </template>
          <el-collapse class="inner">
            <br>
            <video :src="videoSrc.basic" controls width="950" height="540"></video>
          </el-collapse>

          <el-collapse class="inner">
            <br>
            <el-form ref="form" label-width="170px">
             <el-form-item label="请在此处填写你的答案：">
              <el-input placeholder="请在此处填写你的答案" v-model="textarea" type="textarea" :autosize="{ minRows: 4, maxRows: 8}"></el-input>
             </el-form-item>
            </el-form>
          </el-collapse>
        </el-collapse-item>
      </el-collapse>
    </div>
    <!--考生须知对话框-->
    <el-dialog title="面试须知" :visible.sync="dialogVisible" width="30%" v-if="examState==1">
      <span>未经允许禁止转载</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">知道了</el-button>
      </span>
    </el-dialog>

    <div class="title" v-if="examState==2">
      <span >面试模块</span>
      <span>/  结构化面试</span>
    </div>
    <div class="wrapper" v-if="examState==2">
      <ul class="top">
        <li class="example">结构化面试</li>
        <li><i class="iconfont icon-pen-"></i></li>
        <li><i class="iconfont icon-share"></i></li>
        <li class="right">
          <div>
            <span class="count">总分</span>
            <span class="score">{{score[0]+score[1]+score[2]}}</span>
          </div>
        </li>
      </ul>
      <ul class="bottom">
        <li>更新于{{examData.examDate}}</li>
        <li>来自 {{examData.institute}}</li>
        <li class="btn">{{examData.type}}</li>
        <li class="right"><el-button @click="commit()">完成面试</el-button></li>
      </ul>
      <ul class="info">
        <li @click="dialogVisible = true"><a href="javascript:;"><i class="iconfont icon-info"></i>面试须知</a></li>
      </ul>
    </div>
    <div class="content" v-if="examState==2">
      <el-collapse v-model="activeName" >
        <el-collapse-item class="header" name="0">
          <template slot="title" class="stitle">
            <div class="title">
              <span>结构化面试练习</span><i class="header-icon el-icon-info"></i>
              <!--<span class="time">{{examData.totalScore}}分 / {{examData.totalTime}}分钟</span>-->
              <span class="time">100分 / 20分钟</span>
              <el-button type="primary" size="small">点击查看面试详情</el-button>
            </div>
          </template>
          <el-collapse class="inner">
            <br>
            <video :src="videoSrc.structure" controls width="950" height="540"></video>
          </el-collapse>
          <el-collapse class="inner">
            <br>
            <el-form ref="form" label-width="170px">
              <el-form-item label="请在此处填写你的答案：">
                <el-input placeholder="请在此处填写你的答案" v-model="textarea" type="textarea" :autosize="{ minRows: 4, maxRows: 8}"></el-input>
              </el-form-item>
            </el-form>
          </el-collapse>
        </el-collapse-item>
      </el-collapse>
    </div>
    <!--考生须知对话框-->
    <el-dialog title="面试须知" :visible.sync="dialogVisible" width="30%" v-if="examState==2">
      <span>未经允许禁止转载</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">知道了</el-button>
      </span>
    </el-dialog>

    <div class="title" v-if="examState==3">
      <span >面试模块</span>
      <span>/  无领导小组讨论</span>
    </div>
    <div class="wrapper" v-if="examState==3">
      <ul class="top">
        <li class="example">无领导小组讨论</li>
        <li><i class="iconfont icon-pen-"></i></li>
        <li><i class="iconfont icon-share"></i></li>
        <li class="right">
          <div>
            <span class="count">总分</span>
            <span class="score">{{score[0]+score[1]+score[2]}}</span>
          </div>
        </li>
      </ul>
      <ul class="bottom">
        <li>更新于{{examData.examDate}}</li>
        <li>来自 {{examData.institute}}</li>
        <li class="btn">{{examData.type}}</li>
        <li class="right"><el-button @click="commit()">完成面试</el-button></li>
      </ul>
      <ul class="info">
        <li @click="dialogVisible = true"><a href="javascript:;"><i class="iconfont icon-info"></i>读者须知</a></li>
      </ul>
    </div>
    <div class="content" v-if="examState==3">
      <el-collapse v-model="activeName" >
        <el-collapse-item class="header" name="0">
          <template slot="title" class="stitle">
            <div class="title">
              <span>无领导小组讨论练习</span><i class="header-icon el-icon-info"></i>
              <!--<span class="time">{{examData.totalScore}}分 / {{examData.totalTime}}分钟</span>-->
              <span class="time">100分 / 20分钟</span>
              <el-button type="primary" size="small">点击查看面试详情</el-button>
            </div>
          </template>
          <el-collapse class="inner">
            <br>
            <video :src="videoSrc.discussion" controls width="950" height="540"></video>
          </el-collapse>
        </el-collapse-item>
        <el-collapse class="inner">
          <br>
          <el-form ref="form" label-width="170px">
            <el-form-item label="请在此处填写你的回答：">
              <el-input placeholder="请在此处填写你的回答" v-model="textarea" type="textarea" :autosize="{ minRows: 4, maxRows: 8}"></el-input>
            </el-form-item>
          </el-form>
        </el-collapse>
      </el-collapse>
    </div>
    <!--考生须知对话框-->
    <el-dialog title="阅读须知" :visible.sync="dialogVisible" width="30%" v-if="examState==3">
      <span>未经允许禁止转载</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">知道了</el-button>
      </span>
    </el-dialog>


  </div>


</template>

<script>
export default {
  data() {
    return {
      startTime:null,
      endTime:null,
      textarea:'',
      dialogVisible: false, //对话框属性
      activeName: '0',  //默认打开序号
      topicCount: [],//每种类型题目的总数
      score: [],  //每种类型分数的总数
      examState:null,
      videoSrc: {
        basic: require("@/assets/video/basic.mp4"),
        structure: require("@/assets/video/structure.mp4"),
        discussion: require("@/assets/video/discussion.mp4")
      },
      examData: { //考试信息
        // source: null,
        // totalScore: null,
      },
      topic: {  //试卷信息

      },
    }
  },
  mounted() {
    this.init()
  },
  methods: {
    //初始化页面数据
    init() {
      let date = new Date()
      this.startTime = this.getTime(date)
      let examCode = this.$route.query.examCode //获取路由传递过来的试卷编号
      this.$data.examState=this.$route.query.examState //获取路由传递过来的内容编号
      this.$axios(`/api/exam/${examCode}`).then(res => {  //通过examCode请求试卷详细信息
        res.data.data.examDate = res.data.data.examDate.substr(0,10)
        this.examData = { ...res.data.data}
        let paperId = this.examData.paperId
        this.$axios(`/api/paper/${paperId}`).then(res => {  //通过paperId获取试题题目信息
          this.topic = {...res.data}
          let keys = Object.keys(this.topic) //对象转数组
          keys.forEach(e => {
            let data = this.topic[e]
            this.topicCount.push(data.length)
            let currentScore = 0
            for(let i = 0; i< data.length; i++) { //循环每种题型,计算出总分
              currentScore += data[i].score
            }
            this.score.push(currentScore) //把每种题型总分存入score
          })
        })
      })
    },
    getTime(date) { //日期格式化
      let year = date.getFullYear()
      let month= date.getMonth()+ 1 < 10 ? "0" + (date.getMonth() + 1) : date.getMonth() + 1;
      let day=date.getDate() < 10 ? "0" + date.getDate() : date.getDate();
      let hours=date.getHours() < 10 ? "0" + date.getHours() : date.getHours();
      let minutes=date.getMinutes() < 10 ? "0" + date.getMinutes() : date.getMinutes();
      let seconds=date.getSeconds() < 10 ? "0" + date.getSeconds() : date.getSeconds();
      // 拼接
      return year+"-"+month+"-"+day+" "+hours+":"+minutes+":"+seconds;
    },
    toAnswer(id) {
      this.$router.push({path:"/answer",query:{examCode: id}})
    },
    commit() {
      this.$confirm("考试结束时间未到,是否提前交卷","友情提示",{
        confirmButtonText: '立即交卷',
        cancelButtonText: '再检查一下',
        type: 'warning'
      }).then(() => {
        let date = new Date()
        this.endTime = this.getTime(date)
        let myScore
        if (this.textarea == '') {
          myScore = 0
        } else {
          myScore = 80
        }
        this.$router.push({
          path: '/interviewScore', query: {
            score: myScore,
            startTime: this.startTime,
            endTime: this.endTime
          }
        })
      }).catch(() => {
        console.log("继续答题")
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.bottom {
  .right{
    .el-button{
      color: #409EFF;
      border-color: #c6e2ff;
      background-color: #ecf5ff;
    }
  }
}
.right {
  margin-left: auto;
}
.inner .contenti .question {
  margin-left: 40px;
  color: #9a9a9a;
  font-size: 14px;
}
.content .inner .titlei {
  margin-left: 20px;
  font-size: 16px;
  color: #88949b;
  font-weight: bold;
}
.content .title .time {
  font-size: 16px;
  margin-left: 420px;
  color: #999;
}
.content .stitle {
  background-color: #0195ff;
}
.content .title span {
  margin-right: 10px;
}
#msg .content .title {
  font-size: 20px;
  margin: 0px;
  display: flex;
  align-items: center;
}
.content {
  margin-top: 20px;
  background-color: #fff;
}
.content .header {
  padding: 10px 30px;
}
.wrapper .info {
  margin: 20px 0px 0px 20px;
  border-top: 1px solid #eee;
  padding: 20px 0px 10px 0px;
}
.wrapper .info a {
  color: #88949b;
  font-size: 14px;
}
.wrapper .info a:hover {
  color: #0195ff;
}
.wrapper .bottom .btn {
  cursor: pointer;
  padding: 5px 10px;
  border: 1px solid #88949b;
  border-radius: 4px;
}
.wrapper .bottom {
  display: flex;
  margin-left: 20px;
  color: #999;
  font-size: 14px;
  align-items: center;
}
.wrapper .bottom li {
  margin-right: 14px;
}
#msg {
  background-color: #eee;
  width: 980px;
  margin: 0 auto;
}
#msg .title {
  margin: 20px;
}
#msg .wrapper {
  background-color: #fff;
  padding: 10px;
}
.wrapper .top {
  display: flex;
  margin: 20px;
  align-items: center;
}
.wrapper .top .right {
  margin-left: auto;
}
.wrapper .top .example {
  color: #333;
  font-size: 22px;
  font-weight: 700;
}
.wrapper .top li i {
  margin-left: 20px;
  color: #88949b;
}
.wrapper .right .count {
  margin-right: 60px;
  color: #fff;
  padding: 4px 10px;
  background-color: #88949b;
  border-top-left-radius: 4px;
  border-bottom-left-radius: 4px;
  border: 1px solid #88949b;
}
.wrapper .right .score {
  position: absolute;
  left: 53px;
  top: -5px;
  padding: 1px 12px;
  font-size: 20px;
  color: #88949b;
  border: 1px dashed #88949b;
  border-left: none;
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
  font-weight: bold;
}
.wrapper .right div {
  position: relative;
}
</style>
