<template>
  <!-- 用户页面 -->
  <div class="profile">
    <el-row class="profile-mult" style="padding-top: 2em;">
      <el-tabs v-model="activeName" type="card" tab-position="left" @tab-click="handleTabClick">
        <el-tab-pane :disabled="true" label="我的互动" name="0"/>
        <el-tab-pane name="1">
          <span slot="label"><i class="el-icon-coordinate"/> 个人信息</span>
          <div class="padding-main my-info">
            <h1 class="h1"> <i class="el-icon-edit-outline"/> 修改资料</h1>
            <h3>个人账号</h3>
            <div class="info-edit">
              <span>名字</span>
              Jackson
              <el-link icon="el-icon-edit">编辑</el-link>
            </div>
            <div class="info-edit">
              <span>Email</span>
              xxx@qq.com
              <el-link icon="el-icon-edit">编辑</el-link>
            </div>
            <div class="info-edit">
              <span>手机号</span>
              1766711111
              <el-link icon="el-icon-edit">编辑</el-link>
            </div>
            <div class="info-edit">
              <span>居住地</span>
              山东济南
              <el-link icon="el-icon-edit">编辑</el-link>
            </div>
          </div>
        </el-tab-pane>
        <el-tab-pane name="2">
          <span slot="label"><i class="el-icon-mobile-phone"/> 绑定手机</span>
          <div class="padding-main phone">
            <h1 class="h1"> <i class="el-icon-mobile-phone"/> 手机绑定</h1>
            <el-form ref="form" :model="form" label-position="top" label-width="80px">
              <el-form-item label="手机号">
                <el-input
                  v-model="form.name"/>
              </el-form-item>
              <el-form-item label="验证码">
                <el-input v-model="form.name">
                  <template slot="append">获取验证码</template>
                </el-input>
              </el-form-item>
              <el-button style="background-color: #eeeeee;" round>绑定手机</el-button>
            </el-form>
          </div>
        </el-tab-pane>
        <el-tab-pane name="3">
          <span slot="label"><i class="el-icon-lock"/> 修改密码</span>
        </el-tab-pane>
      </el-tabs>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'Profile',
  head() {
    return {
      // title: `${this.isEnLang ? '' : this.$i18n.nav.project + ' | '}的个人主页`
      title: `${this.isEnLang ? '' : ' GuoGuang| '}的个人主页`
    }
  },
  data() {
    return {
      activeName: '1',
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      }
    }
  },
  fetch({ store }) {
    return store.dispatch('project/fetchRepositories')
  },
  computed: {
    isEnLang() {
      return this.$store.getters['global/isEnLang']
    },
    isMobile() {
      return this.$store.state.global.isMobile
    },
    projects() {
      return this.$store.state.project.repositories.data
    }
  },
  methods: {
    handleTabClick(tab, event) {
      console.log(tab, event)
    }
  }
}
</script>

<style lang="scss" scoped>
.profile {
  margin-bottom: 2em;
  .profile-mult {
    .padding-main {
      background: #f8f8f8;
      padding: 2em;
      // border: 1px solid rgba(34,36,38,.15);
    }
    .my-info {
      // border: 1px solid rgba(34,36,38,.15);
      input {
        background-color: #eee;
      }
    }
    .h1 {
      padding-bottom: 0.5em;
      border-bottom: #ddd 1px solid;
      margin-top: 0;
    }
    .info-edit {
      display: flex;
      border-top: #ddd 1px dashed;
      justify-content: space-between;
      padding: 1em;
    }
  }
}
</style>

<style lang="scss">
.profile {
  .phone {
    .el-input {
      width: 60%;
    }
    input {
      background-color: #eee;
    }
  }
  .el-tabs--left {
    .el-tabs__header {
      margin-right: 3em !important;
      background: #f8f8f8;
    }
    .el-tabs__nav {
      border: 1px solid #d3e0e9 !important;
      flex-direction: column;
      display: flex;
      width: 15em;
      transform: translateY(0px);
      .el-tabs__item {
        text-align: center !important;
      }
      .el-tabs__item:hover {
        color: #303133;
      }
    }
  }

  .el-tabs--left.el-tabs--card .el-tabs__item.is-left.is-active {
    border-right-color: #d3e0e9 !important;
    color: #303133 !important;
    background: rgba(0, 0, 0, 0.05);
  }
}
</style>
