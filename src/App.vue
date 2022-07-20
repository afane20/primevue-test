<template>
  <h1>This is a test</h1>
  <Button label="Testing"></Button><br><br>

  <!-- <div>
    <Button type="button" icon="pi pi-plus" label="Expand All" @click="expandAll" />
    <Button type="button" icon="pi pi-minus" label="Collapse All" @click="collapseAll" />
  </div> -->

  <Tree :value="nodes"></Tree><br><br>
  <Tree :value="nodes2"></Tree>
  <pre style="text-align: left">{{ JSON.stringify(rawData, null, 2) }}</pre>
</template>

<script>

import Button from 'primevue/button';
import Tree from 'primevue/tree';
import NodeService from './service/NodeService';
import NodeService2 from './service/NodeService2';
import RawTree from './data/demo-data.json';


export default {
 data() {
        return {
            nodes: null,
            nodes2: null,
            rawData: RawTree
        }
    },
    nodeService: null,
    nodeService2: null,
    created() {
        this.nodeService = new NodeService();
        this.nodeService2 = new NodeService2();
    },
    mounted() {
        this.nodeService.getTreeNodes().then(data => this.nodes = data);
        this.nodeService2.getTreeNodes().then(data => this.nodes2 = data);
    },
  
  name: 'App',
  components: {
    Button, Tree
  }, 
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
