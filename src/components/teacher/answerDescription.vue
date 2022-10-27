<!-- 题库管理功能介绍 -->
<template>
  <section class="description">
    <p class="title">题库管理功能介绍</p>
    <p class="content">该题库包含三种题型，分别为选择题，填空题，判断题，
      其中填空题也可以作为简答题使用，填空题中需要填写几个空格就需要设置几个()，
      如果需要简答则需要在设置题目之后，在题目最后方加上()。这样就组成了一张完整的试卷。
    </p>
  </section>
</template>

<style lang="scss" scoped>
.description {
  margin-left: 40px;
  .title {
    font-size: 22px;
    font-weight: 400;
    color: rgb(31, 47, 61);
  }
  .content {
    width: 600px;
    background-color: #FAF5F2;
    padding: 16px 32px;
    border-radius: 4px;
    border-left: 5px solid #FDC8C8;
    margin: 20px 0px;
  }
}
</style>
