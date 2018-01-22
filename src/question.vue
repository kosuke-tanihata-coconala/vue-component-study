<template>
  <div id="app">
    <dl>
      <dt>相談タイトル</dt>
        <dd>
          <question-edit-vue
            v-if="question.title"
            :initial-value="question.title"
            content-key="title"
            @child-update="childUpdate($event)"
          >
          </question-edit-vue>
        </dd>
      <dt>相談本文</dt>
        <dd>
          <question-edit-vue
            v-if="question.body"
            :initial-value="question.body"
            content-key="body"
            @child-update="childUpdate($event)"
          >
          </question-edit-vue>
        </dd>
        <dt>相談者名</dt>
          <dd>
            <question-edit-vue
            v-if="question.user_name"
            :initial-value="question.user_name"
            content-key="user_name"
            @child-update="childUpdate($event)"
          >
          </question-edit-vue>
          </dd>
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
    childUpdate(columnValue){
        this.question[Object.keys(columnValue)]= Object.values(columnValue)[0]
    }
  }
}
</script>
