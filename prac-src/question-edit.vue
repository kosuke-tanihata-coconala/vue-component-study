<tempalte>
<div>
  <div>
    <span></span>
    <textarea
      class="form-control"
      type="text"
      ref="textarea"
      rows="3"
    ></textarea>
  </div>
</div>
</template>
<script>
  export default {
    // 引数
    props:{},
    // このcoponentsで使用される変数
    data(){},
    methods:{
      // 編集エリアを開ける
      openEditArea(){},
      // 親要素にデータを伝播させる
      applyParent(){}
    }
  }
</script>
