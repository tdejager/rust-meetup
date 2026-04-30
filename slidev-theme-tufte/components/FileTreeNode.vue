<script setup lang="ts">
type Node = {
  name: string
  type?: 'dir' | 'file' | 'link'
  target?: string
  comment?: string
  children?: Node[]
}

defineProps<{ node: Node }>()
</script>

<template>
  <li>
    <div class="row">
      <carbon-folder    v-if="node.type === 'dir'"  class="icon dir" />
      <carbon-link      v-else-if="node.type === 'link'" class="icon link" />
      <carbon-document  v-else                      class="icon file" />
      <span :class="['name', node.type || 'file']">{{ node.name }}</span>
      <span v-if="node.target" class="target">{{ node.target }}</span>
      <span v-if="node.comment" class="comment"># {{ node.comment }}</span>
    </div>
    <ul v-if="node.children && node.children.length">
      <FileTreeNode
        v-for="(child, i) in node.children"
        :key="i"
        :node="child"
      />
    </ul>
  </li>
</template>
