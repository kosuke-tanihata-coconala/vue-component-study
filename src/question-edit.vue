<template>
  <div>
    <span
      v-if="!isEditing"
      @click="openEditArea"
    >{{ value }}
    </span>
    <textarea
      v-else
      @blur="applyParent"
      class="form-control"
      type="text"
      v-model="value"
      ref="textarea"
      rows="3"
    ></textarea>
  </div>
</template>
<script>
  export default {
    // コンポーネントの引数を指定する
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
        this.$nextTick(function () {this.$refs.textarea.focus() });
      },
      // 親要素にデータを伝播させる
      applyParent() {
        this.isEditing = false;
        // $emitメソッドを使う事によってのみ親要素を更新する事ができる
        this.$emit('child-update', { [this.contentKey]: this.value} );
      }
    },
    // 値をwatchして変更があったら親に渡しても良い
    watch: {
       value: {
        deep: true,
        handler(v) {
          this.$emit('change', v);
        }
      }
    }
  }
</script>
