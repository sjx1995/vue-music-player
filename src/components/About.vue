<template>
  <section>
    <div class="close" @click="handleHiddenAbout">返回</div>
    <article class="forYou">
      <h1>这个世界会好吗</h1>
      <p>李志曾说：<br>我很害怕有一天我不爱这个世界了，变得跟其他人一样势力和冷漠</p>
      <br>
      <p>我很害怕他们就这么被遗忘，自己总要做点什么，证明自己来过，证明他们努力过</p>
      <p>愿每一个善待世界的人，都可以被温柔对待</p>
    </article>
    <br>
    <article class="last">
      <p>最后，与君共勉我最爱的一首诗：</p>
      <article class="poetry">
        <h2>回答 · 北岛</h2>
        <p>卑鄙是卑鄙者的通行证，</p>
        <p>高尚是高尚者的墓志铭。</p>
        <p>看吧，在那镀金的天空中，</p>
        <p>飘满了死者弯曲的倒影。</p>
        <br>
        <p>冰川纪过去了，</p>
        <p>为什么到处都是冰凌？</p>
        <p>好望角发现了，</p>
        <p>为什么死海里千帆相竞？</p>
        <br>
        <p>我来到这个世界上，</p>
        <p>只带着纸、绳索和身影，</p>
        <p>为了在审判之前，</p>
        <p>宣读那些被判决了的声音：</p>
        <br>
        <p>告诉你吧，世界，</p>
        <p>我——不——相——信！</p>
        <p>纵使你脚下有一千名挑战者，</p>
        <p>那就把我算做第一千零一名。</p>
        <br>
        <p>我不相信天是蓝的，</p>
        <p>我不相信雷的回声；</p>
        <p>我不相信梦是假的，</p>
        <p>我不相信死无报应。</p>
        <br>
        <p>如果海洋注定要决堤，</p>
        <p>就让所有的苦水都注入我心中；</p>
        <p>如果陆地注定要上升，</p>
        <p>就让人类重新选择生存的峰顶。</p>
        <br>
        <p>新的转机和闪闪的星斗，</p>
        <p>正在缀满没有遮拦的天空，</p>
        <p>那是五千年的象形文字，</p>
        <p>那是未来人们凝视的眼睛。</p>
      </article>
    </article>
  </section>
</template>

<script>
export default {
  name: 'About',
  methods: {
    handleHiddenAbout () {
      this.$emit('hiddenAbout')
    }
  }
}
</script>

<style lang="stylus" type="text/stylus" scoped>
section
  margin 80px auto
  width 720px
  position relative
  div.close
    background-color: #333;
    color: #fff;
    display: inline-block;
    padding: 7px 15px;
    position: fixed;
    top: 70px;
    left: 80px;
    cursor: pointer;
  article.forYou,
  article.last
    h1
      text-align center
      font-size 28px
      font-weight 700
      padding 20px 0
    p
      font-size 18px
      line-height 24px
    article.poetry
      text-align center
      h2
        padding 15px 0
        font-size 20px
        line-height 28px
        font-weight 700
      p
        font-family '楷体'
        font-size 20px
        line-height 24px
</style>