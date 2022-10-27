// 点击试卷后的缩略信息
<template>
  <div id="msg">
    <!--1-->
    <div class="title" v-if="examState==1">
      <span >好文章读背</span>
      <span>/  我们为什么需要良好的家风</span>
    </div>
    <div class="wrapper" v-if="examState==1">
      <ul class="top">
        <li class="example">我们为什么需要良好的家风</li>
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
        <li class="right"><el-button @click="toAnswer(examData.examCode)">开始答题</el-button></li>
      </ul>
      <ul class="info">
        <li @click="dialogVisible = true"><a href="javascript:;"><i class="iconfont icon-info"></i>读者须知</a></li>
      </ul>
    </div>
    <div class="content" v-if="examState==1">
      <el-collapse v-model="activeName" >
        <el-collapse-item class="header" name="0">
          <template slot="title" class="stitle">
            <div class="title">
              <span >我们为什么需要良好的家风</span><i class="header-icon el-icon-info"></i>
              <!--<span class="time">{{examData.totalScore}}分 / {{examData.totalTime}}分钟</span>-->
              <span class="time"></span>
              <el-button type="primary" size="small">点击查看文章详情</el-button>
            </div>
          </template>
          <el-collapse class="inner">
            <font size="4">
              <li>每一个孩子的健康 成长都犹如一棵棵小树苗茁壮成长的历程。不同的只是树苗需要人工制作的木架来扶持它，匡正它的成长轨迹，而孩子们则是需要家长的精心教育与帮助来健康成长。对于那些误入歧途的孩子们，我不敢断定全部都是由于家庭的影响因素对他们造成了负面的影响而产生了恶果，但我确信，对于他们的错误，家庭环境自己家长都有着不可推卸的责任。这时候，家风，家训以及家教的好坏都被最有力地证明!</li>
              <li>在我看来，首先，家风是一种教育方式的传承，它是一种精神层面的教育，是一种需要潜移默化的教育理念。换言之，家风即家庭的一种风气，是一种正面的，积极向上的行为准则。它需要先内化于心，而后外化于日常的行为中。因此，对于孩子的家风教育并不能只停留在表层的行为教育上，更重要的是对孩子的精神教育。表现在日常生活中，就是指不仅仅需要对孩子的行为进行简单的判定正误，更重要的是要告诉其所以然，进而引向教育的核心。如此反复，使家风的存在逐渐进入孩子的内心，形成一种行事的内在准则。再者，家训作为中国自古流传下来的一种家庭传统，至今在我们的生活中仍然有着强烈的影响。相对于家风来说，家训则显得更为具体易懂。它就是对家庭成员的一种要求或者说是一种警示，明确地指出行为方式中的禁区。古人有每日诵其家训并将其熟记于心之礼，细细想来，这种传统也不是全无道理的。熟记于心之后，每当你行事之前便会不自觉地以家训为准，符合则为之，不符则拒为之。事实上，家训的存在是对家风的进一步补充与完善，以达到内外共同要求的目的。最后，是我认为最为重要的一项——家教。它主要是以父母双方为主导的对孩子的亲身教育。这种教育是其他任何人所不能代替的。可以说，家风与家训的教育都是家教内容的一部分。家教内容体现在孩子成长过程中的每一分每一秒。家庭环境的好坏直接影响孩子人生观、价值观以及世界观的形成。当然，家教的成功与否也能直接反映出你是否是一名合格的负责人的家长。尤其是在孩子的认知阶段，他们所有的认知标准都来自于父母对他们的引导，所以这段时期是至关重要的。人生观、价值观以及世界观一旦形成，是很难再改变的。因此孩子的一生与家庭教育的质量真的是密不可分的。要想自己的孩子能够有一个好的未来，首先作为家长的我们就应该从现在做起，给他们一个好的家庭环境，好的家庭教育。</li>
              <li>家风不是说说而已，家训也不是背熟就作罢，家教更不是简单粗暴的打骂。作为一名合格的家长，我们必须首先自己要重视这三者的存在，而后才能将其运用到对孩子的教育中。家风正不正，家训严不严，家教好不好，不是别人说了算，自己孩子的未来才是最好的证明。不要等到无可挽救的地步再后悔自己当初教育的懒惰与放纵，要从现在开始担负起自己为人父母的责任，百分百地投入自己的爱给孩子，给自己以严格的要求，以高标准的家庭教育助孩子成就美好的未来。</li>
            </font>
          </el-collapse>
        </el-collapse-item>
      </el-collapse>
    </div>
    <!--考生须知对话框-->
    <el-dialog title="阅读须知" :visible.sync="dialogVisible" width="30%" v-if="examState==1">
      <span>未经允许禁止转载</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">知道了</el-button>
      </span>
    </el-dialog>

    <!--2-->
    <div class="title" v-if="examState==2">
      <span >名人名句读背</span>
      <span>/  与肝胆人共事，无字句处读书</span>
    </div>
    <div class="wrapper" v-if="examState==2">
      <ul class="top">
        <li class="example">与肝胆人共事，无字句处读书</li>
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
        <li class="right"><el-button @click="toAnswer(examData.examCode)">开始答题</el-button></li>
      </ul>
      <ul class="info">
        <li @click="dialogVisible = true"><a href="javascript:;"><i class="iconfont icon-info"></i>读者须知</a></li>
      </ul>
    </div>
    <div class="content" v-if="examState==2">
      <el-collapse v-model="activeName" >
        <el-collapse-item class="header" name="0">
          <template slot="title" class="stitle">
            <div class="title">
              <span>周恩来的名言警句</span><i class="header-icon el-icon-info"></i>
              <!--<span class="time">{{examData.totalScore}}分 / {{examData.totalTime}}分钟</span>-->
              <span class="time"></span>
              <el-button type="primary" size="small">点击查看文章详情</el-button>
            </div>
          </template>
          <el-collapse class="inner">
            <font size="4">
              <li>与肝胆人共事，无字句处读书。</li>
              <li>我们爱我们的民族，这是我们自信心的来源。</li>
              <li>一帆风顺是不能磨练人的。</li>
              <li>今天的现实是不够美满的，但是美满的现实需要我们大家共同去创造。</li>
              <li>我们的下一代，总是要把自己摆在劳苦大众一起，要能够吃得起苦。因为我们的革命精神，就是从吃苦中得来的!</li>
              <li>为中华之崛起而读书。</li>
              <li>浮舟沧海，立马昆仑。</li>
            </font>
          </el-collapse>
        </el-collapse-item>
      </el-collapse>
    </div>
    <!--考生须知对话框-->
    <el-dialog title="阅读须知" :visible.sync="dialogVisible" width="30%" v-if="examState==2">
      <span>未经允许禁止转载</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">知道了</el-button>
      </span>
    </el-dialog>

    <!--3-->
    <div class="title" v-if="examState==3">
      <span >焦点和热点新闻社评</span>
      <span>/  希腊学者读中共二十大报告: 中国是全人类稳定和发展的因素</span>
    </div>
    <div class="wrapper" v-if="examState==3">
      <ul class="top">
        <li class="example">希腊学者读中共二十大报告: 中国是全人类稳定和发展的因素</li>
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
        <li class="right"><el-button @click="toAnswer(examData.examCode)">开始答题</el-button></li>
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
              <span>中国共产党第二十次全国代表大会</span><i class="header-icon el-icon-info"></i>
              <!--<span class="time">{{examData.totalScore}}分 / {{examData.totalTime}}分钟</span>-->
              <span class="time"></span>
              <el-button type="primary" size="small">点击查看文章详情</el-button>
            </div>
          </template>
          <el-collapse class="inner">
            <font size="4">
              <li>
              2022年无疑是现代世界历史上的关键时刻，正在发生的事件在推动国际体系的权力转移，与二战后创造的局面相比，当今世界存在着引发严重安全问题的可能。疫情、乌克兰危机，以及西方制裁俄罗斯造成的后果，与发生在欧盟内部的能源危机相叠加，正在引发西方世界政治、经济和社会的不稳定。
              </li>
              <li>
              在政治层面，许多西方国家政府在应对挑战方面表现得不稳定且效率低下，最近的典型例子就是英国。在经济层面，高通胀和能源危机在西方引发动荡。在社会层面，前所未有的“贫困化”导致社会更加不稳定，没有人能够预测未来，西方世界似乎迷失了方向。
              </li>
              <li>
              在这种多变的国际环境下，在中国共产党的领导下，中国正在有计划地应对二十一世纪的全球性挑战，坚持原则，展望未来，为的是建成一个现代化国家，一个繁荣的社会主义社会。
              </li>
              <li>
              中共二十大报告中，对未来五年的行动计划进行了整体分析，涵盖了政治、经济和社会生活的方方面面，极其详细地提出了中国共产党对未来的规划和愿景。从报告中可以看出，已经谋划并即将实施的改革，既关系到中国共产党，也关系到经济、社会、外交和国际合作。
              </li>
              <li>
              事实证明，中国的今天和未来，离不开中国共产党的领导和中国人民的奋斗。中国共产党是全球最大的执政党。自成立以来，中国共产党无论在运作和决策机制方面，还是党员能力和专业性上，都在不断发展。中国共产党高度重视消除党内腐败，因为腐败是党的活力和效能的“毒瘤”。同时，中国实行全过程人民民主，保障人民参与选举和决策。
              </li>
              <li>
              在国际层面，中国再次明确表示，永远不称霸、永远不搞扩张，坚持在和平共处五项原则基础上同各国发展友好合作。美国意图制造新冷战格局，将国际社会分为西方和东方，是美国试图强加给盟友（主要是欧盟）的一个关键工具。因为他们认为，西方与中国在各个层面的脱钩将延缓中国进一步发展。相反，中国明确推行以世界和平、共同发展为目标的独立自主的外交政策，并以身作则坚持经济全球化。
              </li>
              <li>
              在社会层面，报告指出要完善分配制度，促进机会公平，增加低收入者收入，扩大中等收入群体，规范收入分配秩序，规范财富积累机制。这将增进人民的福祉。在我们目睹西方社会，特别是中产阶级走向贫困的时刻，中共旨在减少社会和收入不平等的目标是一项极为重要的政治决策，将对社会繁荣作出贡献。
              </li>
              <li>
              在国际体系尚不稳定的今天，中国以积极的态度看待和规划未来，是全人类稳定和发展的因素。应该认识到，当今最重要的是，人类作为一个整体面临的问题太大，且无法由单个国家独自应对。世界和平、人民福祉、气候危机……这些无疑是全人类必须面对的问题，没有人可以置身事外，这与意识形态无关。
              </li>
            </font>
          </el-collapse>
        </el-collapse-item>
      </el-collapse>
    </div>
    <!--考生须知对话框-->
    <el-dialog title="阅读须知" :visible.sync="dialogVisible" width="30%" v-if="examState==3">
      <span>未经允许禁止转载</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">知道了</el-button>
      </span>
    </el-dialog>

    <div class="title" v-if="examState==4">
      <span >思维方法学习</span>
      <span>/  唯物辩证法</span>
    </div>
    <div class="wrapper" v-if="examState==4">
      <ul class="top">
        <li class="example">唯物辩证法</li>
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
        <li class="right"><el-button @click="toAnswer(examData.examCode)">开始答题</el-button></li>
      </ul>
      <ul class="info">
        <li @click="dialogVisible = true"><a href="javascript:;"><i class="iconfont icon-info"></i>读者须知</a></li>
      </ul>
    </div>
    <div class="content" v-if="examState==4">
      <el-collapse v-model="activeName" >
        <el-collapse-item class="header" name="0">
          <template slot="title" class="stitle">
            <div class="title">
              <span>唯物辩证思维方法学习</span><i class="header-icon el-icon-info"></i>
              <!--<span class="time">{{examData.totalScore}}分 / {{examData.totalTime}}分钟</span>-->
              <span class="time"></span>
              <el-button type="primary" size="small">点击查看文章详情</el-button>
            </div>
          </template>
          <el-collapse class="inner">
            <font size="4">
              <li>
                归纳与演绎是最初的也是最基本的思维方法。归纳是从个别到一般的方法，即从个别事实中概括! -一般原理。演绎是从一般到个别的万法，即从一般原理推论一个别结论。归纳和演经的客
                观基础是事物本身固有的个性和共性、特殊和晋遍的关系。归纳和演绎是辩证统一关系:归纳是演绎的基础，演绎是归纳的前提。在实际的思维过程中，归纳和演绎相互补充，交替使用。
              </li>
              <li>
                分析与综合是一种更为深刻的思维方法。分析是在思维过程中把认识的对象分解为不同的组成部部分、方面、特性等，对它们分别加以研究，认识事物的各个方面，从中找出基础的部分、本质的方面，综合是把分解出来的不同部分、方面按其客观的次序、结构组成一个整体，从而达到对事物整体的认识。
              </li>
              <li>
                抽象与具体是辩证思维的高级形式。抽象是对客观事物某一方面本质的概括或规定，思维具体或理性具体是在抽象的基础上形成的综合，它不同于感性具体。感性具体只是感官直接感觉到的具体，而理性具体是在感性具体基础上经过思维的分析与综合，达到对事物多方面属性或本质的把已握。
              </li>
              <li>
                逻辑与历史的统一。由抽象上升到事体的逻辑思维过程同客观事物的历史过程和认识的历史过程应当符合，也就是逻辑和历史的统一。逻辑与历史相统一，是从抽象上升到具体的内在要
                求。逻辑指的是理性思维或抽象思维，它以理论的形态反映客观事物的规律性。
              </li>
            </font>
          </el-collapse>
        </el-collapse-item>
      </el-collapse>
    </div>
    <!--考生须知对话框-->
    <el-dialog title="阅读须知" :visible.sync="dialogVisible" width="30%" v-if="examState==4">
      <span>未经允许禁止转载</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">知道了</el-button>
      </span>
    </el-dialog>

    <div class="title" v-if="examState==5">
      <span >学习成功测试</span>
      <span>/  小测试</span>
    </div>
    <div class="wrapper" v-if="examState==5">
      <ul class="top">
        <li class="example">小测试</li>
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
        <li class="btn">小测试</li>
        <li class="right"><el-button @click="toAnswer(examData.examCode)">开始答题</el-button></li>
      </ul>
      <ul class="info">
        <li @click="dialogVisible = true"><a href="javascript:;"><i class="iconfont icon-info"></i>测试须知</a></li>
      </ul>
    </div>
    <div class="content" v-if="examState==5">
      <el-collapse v-model="activeName" >
        <el-collapse-item class="header" name="0">
          <template slot="title" class="stitle" >
            <div class="title">
              <span>学习小测试</span><i class="header-icon el-icon-info"></i>
              <span class="time">{{examData.totalScore}}分 / {{examData.totalTime}}分钟</span>
              <el-button type="primary" size="small">点击查看试题详情</el-button>
            </div>
          </template>
          <el-collapse class="inner">
            <el-collapse-item>
              <template slot="title" name="1">
                <div class="titlei">选择题 (共{{topicCount[0]}}题 共计{{score[0]}}分)</div>
              </template>
              <div class="contenti">
                <ul class="question" v-for="(list, index) in topic[1]" :key="index">
                  <li>{{index+1}}. {{list.question}} {{list.score}}分</li>
                </ul>
              </div>
            </el-collapse-item>
            <el-collapse-item>
              <template slot="title" name="2">
                <div class="titlei">填空题 (共{{topicCount[1]}}题  共计{{score[1]}}分)</div>
              </template>
              <div class="contenti">
                <ul class="question" v-for="(list, index) in topic[2]" :key="index">
                  <li>{{topicCount[0]+index+1}}.{{list.question}}  {{list.score}}分</li>
                </ul>
              </div>
            </el-collapse-item>
            <el-collapse-item>
              <template slot="title" name="3">
                <div class="titlei">判断题 (共{{topicCount[2]}}题 共计{{score[2]}}分)</div>
              </template>
              <div class="contenti">
                <ul class="question" v-for="(list, index) in topic[3]" :key="index">
                  <li>{{topicCount[0]+topicCount[1]+index+1}}. {{list.question}} {{list.score}}分</li>
                </ul>
              </div>
            </el-collapse-item>
          </el-collapse>
        </el-collapse-item>
      </el-collapse>
    </div>
    <!--考生须知对话框-->
    <el-dialog title="阅读须知" :visible.sync="dialogVisible" width="30%" v-if="examState==5">
      <span>好好学习，天天向上</span>
      <span slot="footer" class="dialog-footer">
        <el-button @click="dialogVisible = false">知道了</el-button>
      </span>
    </el-dialog>

    <div class="title" v-if="examState==6">
      <span >视频答疑</span>
      <span>/  习题讲解</span>
    </div>
    <div class="wrapper" v-if="examState==6">
      <ul class="top">
        <li class="example">习题讲解</li>
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
        <li class="right"><el-button @click="toAnswer(examData.examCode)">开始答题</el-button></li>
      </ul>
      <ul class="info">
        <li @click="dialogVisible = true"><a href="javascript:;"><i class="iconfont icon-info"></i>读者须知</a></li>
      </ul>
    </div>
    <div class="content" v-if="examState==6">
      <el-collapse v-model="activeName" >
        <el-collapse-item class="header" name="0">
          <template slot="title" class="stitle">
            <div class="title">
              <span>宋浩的精彩讲解</span><i class="header-icon el-icon-info"></i>
              <!--<span class="time">{{examData.totalScore}}分 / {{examData.totalTime}}分钟</span>-->
              <span class="time"></span>
              <el-button type="primary" size="small">点击查看视频详情</el-button>
            </div>
          </template>
          <el-collapse class="inner">
            <br>
            <video :src="videoSrc.video" controls width="950" height="540"></video>
          </el-collapse>
        </el-collapse-item>
      </el-collapse>
    </div>
    <!--考生须知对话框-->
    <el-dialog title="阅读须知" :visible.sync="dialogVisible" width="30%" v-if="examState==6">
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
      dialogVisible: false, //对话框属性
      activeName: '0',  //默认打开序号
      topicCount: [],//每种类型题目的总数
      score: [],  //每种类型分数的总数
      examState:null,
      videoSrc: {
        video: require("@/assets/video/songhao.mp4")
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
    toAnswer(id) {
      this.$router.push({path:"/answer",query:{examCode: id}})
    },
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
