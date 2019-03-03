<template>
  <v-container>
    <v-layout
      wrap
    >
     <v-sheet
        class="d-flex mt-auto"
        v-for="item in items" 
        :key="item.title"
        :color="item.color"
        height="300"
        max-width="300"
        min-width="150"
     >
        <sheet-footer>
        {{item.title}}
        </sheet-footer>
     </v-sheet>
    </v-layout>
    <v-layout>
      <v-select
        v-model="model"
        :items="color"
        :search-input.sync="search"
        hide-selected
        full-width
        hint="目前最多只能选择一个颜色哦"
        label="请选择您喜欢的颜色"
        dense
        small-chips
    >
      </v-select>
    <v-btn color="success" @click=";">提交</v-btn>
   </v-layout>
  </v-container>
</template>

<script>
export default {
    name:"ThemeManagement",
    data() {
        return {
             model: ['默认蓝色'],
             search: null,
             color:["紫色","黄色","蓝色","黑色","红色","灰色",],
                items:[
                    {
                        title:"紫色",
                        color:"purple"
                    },
                    {
                        title:"黄色",
                        color:"yellow"
                    },
                    {
                        title:"蓝色",
                        color:"blue"
                    },
                    {
                        title:"黑色",
                        color:"black"
                    },
                    {
                        title:"红色",
                        color:"red"
                    },
                    {
                        title:"灰色",
                        color:"grey"
                    },
                ]
        }
    },
    components: {
      SheetFooter: {
        functional: true,

        render (h, { children }) {
          return h('v-sheet', {
            staticClass: 'mt-auto align-center justify-center d-flex',
            props: {
              color: 'rgba(0, 0, 0, .36)',
              dark: true,
              height: 50
            }
          }, children)
        }
      }
    },
    watch: {
      model (val) {
        if (val.length > 1) {
          this.$nextTick(() => this.model.pop())
        }
      }
    }
}
</script>
