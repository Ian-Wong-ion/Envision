<template>
  <v-list two-line subheader>
    <div v-for="setting in settings" :key="setting.id">
      <v-subheader inset>
        {{ setting.name }}
      </v-subheader>
      <v-list-tile v-for="item in setting.items" :key="item.id"  @click=";" avatar>
        <v-list-tile-avatar>
          <v-icon :class="[item.iconClass]">{{ item.icon }}</v-icon>
        </v-list-tile-avatar>
        <v-list-tile-content>
          <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          <v-list-tile-sub-title>{{ item.subtitle }}</v-list-tile-sub-title>
        </v-list-tile-content>
        <v-list-tile-action>
          <v-btn icon ripple :to="item.link">
            <v-icon color="grey lighten-1">keyboard_arrow_right</v-icon>
          </v-btn>
        </v-list-tile-action>
      </v-list-tile>
      <v-divider inset v-if="settings.indexOf(setting) < settings.length - 1"></v-divider>
    </div>
  </v-list>
</template>

<script>

export default {
  name:'SettingList',
  data(){
    return {
      settings: [
        {
          id: 0,
          name: '基本设置',
          items: [
            {id: 0, title: '菜单管理', subtitle: '定义你的个人菜单栏', iconClass: 'yellow white--text', link:'/MenuManagement'},
            {id: 1, title: '标签管理', subtitle: '选择你喜欢的标签，因问将推送你感兴趣的内容', iconClass: 'yellow white--text',link:'/Tagsmanagement'},
            {id: 2, title: '主题管理', subtitle: '选择你喜欢的颜色，因问将生成相应的皮肤', iconClass: 'yellow white--text',link:'/ThemeManagement'},
            
          ]
        },
        {
          id: 1,
          name: '账号设置',
          items: [
            {id: 0, title: '编辑资料',  iconClass: 'info white--text', link:'/'},
            {id: 1, title: '密码设置',  iconClass: 'info white--text', link:'/PasswordManagement'},
            {id: 2, title: '绑定邮箱',  iconClass: 'info white--text', link:'/EmailManagement'},
          ]
        },
        
      ]
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
