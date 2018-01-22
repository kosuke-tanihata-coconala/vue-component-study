<template>
  <div>
    <span
      v-if="!isEditing"
      @click="openEditArea"
    >{{ value }}</span>
    <textarea
      v-else
      @blur="applyParent"
      class="form-control"
      type="text"
      v-model="value"
      ref="ref"
      rows="3"
    ></textarea>
  </div>
</template>
<script>
  export default {
    // メソッドの引数を指定する
    props: {
      initialValue: {
        type: String,
        required: true
      },
      contentKey: {
        type: String,
        required: true
      }
    },
    //　使用する変数を宣言する
    data() {
      // componentの中で使う際には必ずreturnを書く
      return {
        value: this.initialValue,
        isEditing: false
      }
    },
    methods: {
      // 編集エリアを開ける
      openEditArea(){
        this.isEditing = true;
        // データ更新によりdom変更が終わった後に呼ばれるメソッド
        this.$nextTick(function () { this.$refs.ref.focus() });
      },
      // 親要素にデータを伝播させる
      applyParent() {
        this.isEditing = false;
        // $emitメソッドを使う事によってのみ親要素を更新する事ができる
        this.$emit('child-update', { [this.contentKey]: this.value} );
      }
    }
  }
</script>
