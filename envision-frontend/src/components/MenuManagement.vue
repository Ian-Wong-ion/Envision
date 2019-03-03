<template>
    <div>
        
        <v-list class="pt-0">
            
            <v-list-tile v-for="bar in menu" :key="bar.title" @click="dialog = true" avatar>
                <v-list-tile-avatar>
                    <v-icon :class="[bar.iconClass]">{{bar.icon}}</v-icon>
                </v-list-tile-avatar>
                <v-list-tile-content>
                <v-list-tile-title>{{bar.title}}</v-list-tile-title>
                </v-list-tile-content>
            </v-list-tile>
           
        </v-list>
        <v-dialog v-model="dialog" max-width="300">
        <v-card>
            <v-card-title class="headline">是否显示本菜单项？</v-card-title>

            <v-card-text>
            选择不显示后，你将在左侧导航菜单中隐藏本菜单项。
            </v-card-text>

            <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="error darken-1" @click="dialog = false"  >
                不显示
            </v-btn>
            <v-btn color="info darken-1" @click="dialog = false;"  >
                显示
            </v-btn>
            </v-card-actions>
        </v-card>
        </v-dialog>
    </div>
</template>

<script>
export default {
     name:'MenuManagement',
     data() {
        return {
            dialog: false,
             menu: [
                {
                    title: "首页",
                    icon: "home",
                    iconClass: 'info white--text',
                     
                },
                {
                    title: "学习",
                    icon: "school",
                    iconClass: 'info white--text',
                    
                },
                {
                    title: "论坛",
                    icon: "forum",
                    iconClass: 'info white--text',
                    
                },
                {
                    title: "探索",
                    icon: "public",
                    iconClass: 'info white--text',
                    
                },
                {
                    title: "个人中心",
                    icon: "account_circle",
                    iconClass: 'info white--text',
                    
                },
                {
                    title: "创作",
                    icon: "edit",
                    iconClass: 'info white--text',
                    
                },
                {
                    title: "群组",
                    icon: "group",
                    iconClass: 'info white--text',
                   
                },
                {
                    title: "礼品店",
                    icon: "shopping_cart",
                    iconClass: 'info white--text',
                    
                },
                {
                    title: "社团事务",
                    icon: "assignment",
                    iconClass: 'info white--text',
                   
                },
                {
                    title: "管理后台",
                    icon: "build",
                    iconClass: 'info white--text',
                    
                },
            ],
        }
     }
}
</script>
