<template>
  <baklava-editor :plugin="viewPlugin"></baklava-editor>
</template>

<script>
import { Editor, NodeBuilder } from '@baklavajs/core'
import { ViewPlugin } from '@baklavajs/plugin-renderer-vue'

export default {
  data () {
    return {
      editor: new Editor(),
      viewPlugin: new ViewPlugin()
    }
  },
  created () {
    this.editor.use(this.viewPlugin)
    this.createNode()
    // register your nodes, node options, node interface types, ...
  },
  methods: {
    createNode () {
      const myNode = new NodeBuilder('My Node')
        .addInputInterface('My Interface')
        .build()
      this.editor.registerNodeType('My Node', myNode)
    }
  }
}
</script>
