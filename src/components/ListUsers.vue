<template>
  <div class="list-users-block">
      <RecycleScroller
              class="scroller"
              :items="users"
              :item-size="25"
              :buffer="50"
              key-field="id"
              v-slot="{ item }"
      >
          <div class="user" :class="{ selected: item.id === selectedKey }" @click="getUser(item.id)">
              <i class="fas fa-user text-primary mr-1"></i>
              {{ item.name }}
          </div>
      </RecycleScroller>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';
import { RecycleScroller } from 'vue-virtual-scroller';
import 'vue-virtual-scroller/dist/vue-virtual-scroller.css';

@Component({
    components: {
        RecycleScroller,
    },
})
export default class ListUsers extends Vue {
  @Prop(Array) public readonly users!: any[];

  private selectedKey = 0;

  protected getUser(id: number) {
    this.selectedKey = id;
    this.$emit('selectUser', this.users[this.selectedKey]);
  }
}
</script>

<style scoped lang="scss">
  .list-users-block {
    height: 200px;
    overflow-y: auto;
    border: 1px solid #d2d2d2;
  }
  ul {
    padding: 0;
    margin-left: 0;
  }
  li {
    /*background: url("arrow.png") 0 50% no-repeat;*/
    list-style-type: none;
    padding-left: 12px;
    cursor: pointer;
  }

  .scroller {
    height: 100%;
  }

  .user {
    cursor: pointer;
    height: 32%;
    padding: 0 12px;
    display: flex;
    align-items: center;
  }
</style>
