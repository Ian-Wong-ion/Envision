<template>
  <div>
      <v-subheader>请选择您喜欢的标签</v-subheader>
        <v-combobox
          v-model="chips"
          :items="items"
          label="这里将为您展示您选中的标签"
          chips
          color="primary"
          clearable
          append-icon="edit"
          flat
          solo
          full-width
          multiple
        >
          <template slot="selection" slot-scope="data">
            <v-chip
              :selected="data.selected"
              close
              color="green"
              @input="remove(data.item)"
            >
              <strong>{{ data.item }}</strong>&nbsp;
              <span>(已选)</span>
            </v-chip>
          </template>
        </v-combobox>
    <v-layout align-end justify-end>
        <v-btn color="success" @click=";">提交</v-btn>
    </v-layout>       
  </div>
</template>


<script>
  export default {
    data () {
      return {
        chips: ['Programming', 'Playing video games', 'Watching movies', ],
        items: ['Streaming', 'Eating','Programming', 'Playing video games', 'Watching movies', 'Sleeping','C++','unity','C','sleeping','python']
      }
    },

    methods: {
      remove (item) {
        this.chips.splice(this.chips.indexOf(item), 1)
        this.chips = [...this.chips]
      }
    }
  }
</script>