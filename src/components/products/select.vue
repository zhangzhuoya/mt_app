<template>
<el-dropdown>
  <span class="el-dropdown-link">
   {{name}}<i class="el-icon-arrow-down el-icon--right"></i>
  </span>
  <el-dropdown-menu slot="dropdown" >
    <el-dropdown-item  class="dmenu" v-for="(item, index) in list" :key="index">{{item.name}}</el-dropdown-item>
  </el-dropdown-menu>
</el-dropdown>

</template>
<script>
export default {
  props: [
    'name',
    'list'
  ]
}
</script>
<style lang="scss" scoped>
.el-dropdown{
    margin: 0px 81px 10px 0px;

}

</style>
