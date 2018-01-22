<tempalte>
<div>
    <div>
    <span></span>
    <textarea
      class="form-control"
      type="text"
      ref="ref"
      rows="3"
    ></textarea>
  </div>
</div>
</template>
<script>
  export default {
    props:{},
    data(){},
    methods:{
      // 編集エリアを開ける
      openEditArea(){},
      // 親要素にデータを伝播させる
      applyParent(){}
    }
  }
</script>
