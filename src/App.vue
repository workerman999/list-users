<template>
  <div id="app">
    <div class="container">
      <div class="row users-block">
        <div class="col-4">
          <ListUsers :users="users" @selectUser="selected"/>
        </div>
        <div class="col-8">
          <InfoUser :user="user" :avatar="avatar"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import ListUsers from './components/ListUsers.vue';
import InfoUser from './components/InfoUser.vue';

@Component({
  components: {
    ListUsers,
    InfoUser,
  },
})

export default class App extends Vue {
  public user: object = {name: '', company: '', position: '', department: '', active: false};
  private users: any[] = [
    {id: 1, name: 'Пользователь 1', company: 'Компания 1', position: 'Должность 1', department: 'Отдел 1', active: true},
    {id: 2, name: 'Пользователь 2', company: 'Компания 2', position: '', department: 'Отдел 2', active: true},
    {id: 3, name: 'Пользователь 3', company: 'Компания 3', position: 'Должность 3', department: 'Отдел 3', active: false},
    {id: 4, name: 'Пользователь 4', company: 'Компания 4', position: 'Должность 4', department: 'Отдел 4', active: true},
    {id: 5, name: 'Пользователь 5', company: '', position: 'Должность 5', department: 'Отдел 5', active: true},
    {id: 6, name: 'Пользователь 6', company: 'Компания 6', position: 'Должность 6', department: 'Отдел 6', active: true},
    {id: 7, name: 'Пользователь 7', company: 'Компания 7', position: 'Должность 7', department: 'Отдел 7', active: false},
    {id: 8, name: 'Пользователь 8', company: 'Компания 8', position: 'Должность 8', department: 'Отдел 8', active: true},
    {id: 9, name: 'Пользователь 9', company: '', position: '', department: 'Отдел 9', active: true},
    {id: 10, name: 'Пользователь 10', company: 'Компания 10', position: 'Должность 10', department: 'Отдел 10', active: true},
    {id: 11, name: 'Пользователь 11', company: 'Компания 11', position: 'Должность 11', department: 'Отдел 11', active: true},
    {id: 12, name: 'Пользователь 12', company: 'Компания 12', position: 'Должность 12', department: 'Отдел 12', active: false},
    {id: 13, name: 'Пользователь 13', company: 'Компания 13', position: 'Должность 13', department: 'Отдел 13', active: true},
    {id: 14, name: 'Пользователь 14', company: 'Компания 14', position: 'Должность 14', department: 'Отдел 14', active: true},
    {id: 15, name: 'Пользователь 15', company: 'Компания 15', position: 'Должность 15', department: 'Отдел 15', active: false},
  ];
  private avatars: any[] = [1, 2, 3];
  private avatar: number = 0;

  protected selected(data: object): void {
    this.user = data;
    this.randAvatar(this.avatars);
  }

  private randAvatar(arr: any[]): void {
    const rand = Math.floor(Math.random() * arr.length);
    this.avatar = arr[rand];
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.selected {
  background-color: #94e7ff;
}
</style>
