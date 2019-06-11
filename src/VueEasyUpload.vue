<template>
  <div class="vue-upload-wrap">
    <label class="btn" :class="btnStyle" for="file">
      {{btnText}}
    </label>
    <input type="file" name="file" id="file" class="upload-input" accept="" />
    <ul class="vue-upload-list">
      <li></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'vue-easy-upload',
  props: {
    'btnText':{
      default:() => {
        return '上传';
      }
    },
    'btnStyle':{
      default:() => {
        return '';
      }
    },
    'accept':{
      default:() => {
        return '';
      }
    },
    'values':{
      default:() => {
        return [];
      }
    }
  },
  data () {
    return {
      file:this.files
    }
  },
  mounted () {
  },
  computed: {
    switchStatusClass (){
      return this.realValue ? 'on' : 'off';
    }
  },
  watch: {
    value (value) {
      this.realValue = value;
    },
    realValue (value) {
      this.$emit('input', value);
    }
  },
  methods: {
  }
}
</script>

<style scoped>
.vue-upload-wrap{
}
.vue-upload-wrap .btn {

}
.vue-upload-wrap .upload-input {
  background: rgba(255, 255, 255, 0);
  overflow: hidden;
  position: fixed;
  width: 1px;
  height: 1px;
  z-index: -1;
  opacity: 0;
}
</style>

