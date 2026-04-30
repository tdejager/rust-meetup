<script setup lang="ts">
type Node = {
  name: string
  type?: 'dir' | 'file' | 'link'
  target?: string
  comment?: string
  children?: Node[]
}

defineProps<{ tree: Node[]; rootLabel?: string }>()
</script>

<template>
  <div class="file-tree">
    <div v-if="rootLabel" class="row">
      <carbon-folder class="icon dir" />
      <span class="name dir">{{ rootLabel }}</span>
    </div>
    <ul class="root">
      <FileTreeNode
        v-for="(node, i) in tree"
        :key="i"
        :node="node"
      />
    </ul>
  </div>
</template>

<style scoped>
.file-tree {
  font-family: var(--tufte-mono, 'IBM Plex Mono', monospace);
  font-size: 0.78rem;
  line-height: 1.55;
  color: var(--tufte-text, #111);
}
.file-tree :deep(.row) {
  display: flex;
  align-items: center;
  gap: 0.4rem;
}
.file-tree :deep(.icon) {
  flex-shrink: 0;
  width: 0.95rem;
  height: 0.95rem;
}
.file-tree :deep(.icon.dir)  { color: #c9a227; }
.file-tree :deep(.icon.file) { color: #4a4a4a; }
.file-tree :deep(.icon.link) { color: #c14a26; }
.file-tree :deep(.name)      { font-weight: 500; }
.file-tree :deep(.name.dir)  { color: #8a6d00; }
.file-tree :deep(.target)    { color: #777; font-style: italic; }
.file-tree :deep(.target::before) { content: '→ '; color: var(--tufte-accent, #c14a26); }
.file-tree :deep(.comment)   { color: #888; font-style: italic; margin-left: 0.6rem; }
.file-tree :deep(ul) {
  list-style: none;
  margin: 0;
  padding: 0 0 0 1.1rem;
  border-left: 1px dotted #c8c8be;
}
.file-tree :deep(.root) {
  border-left: none;
  padding-left: 0.2rem;
}
</style>
