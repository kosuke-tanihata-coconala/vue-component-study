<template>
  <div>
    <dl>
      <dt>相談タイトル</dt>
      <dd></dd>

      <dt>相談本文</dt>
      <dd></dd>

      <dt>相談者名</dt>
      <dd></dd>
    </dl>
  </div>
</template>
<script>
import questionEditVue from './question-edit.vue';

export default {
  components: {
    questionEditVue
  },
  name: 'app',
  data () {
    return {
      question :{
        title: '共有道路の使用方法に関する覚書',
        body : '隣地が売りに出ていましたが、売れたようで不動産業者から共有道路についての使用方法についての覚書締結を求められています。その中に下記の一文がありますが、内容が理解できません。もしも不利な内容だといけませんので、この件についてお答えいただけますと幸いです。よろしくお願いします。',
        user_name : '匿名太郎'
      }
    }
  },
  methods:{
    // 子要素からのデータの更新を受け付ける
    childUpdate(){
    }
  }
}


</script>
