<template>
  <div class="row">
    <div class="col-12 info-user selected">
      <div class="row">
        <div class="col-6 name-user my-2">
          {{user.name}}
        </div>
      </div>
    </div>
    <div class="col-12 info-user mt-3">
      <div class="row">
        <div class="col-2">
          <div class="avatar" :style="{backgroundImage:`url(${require(`../assets/avatars/${avatar}.png`)})`}"></div>
          <span :class="{online: checkOnline, offline: checkOffline}">&#9899;</span>
        </div>
        <div class="col-10">
          <div class="content ml-3">
            <table>
              <tbody>
              <tr>
                <td width="30%">Должность</td>
                <td class="personal-info" :class="{ fontBold: checkUserPosition }">{{userPosition}}</td>
              </tr>
              <tr>
                <td>Отдел</td>
                <td class="personal-info" :class="{ fontBold: checkUserDepartment }">{{userDepartment}}</td>
              </tr>
              <tr>
                <td>Компания</td>
                <td class="personal-info" :class="{ fontBold: checkUserCompany }">{{userCompany}}</td>
              </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class InfoUser extends Vue {
  @Prop(Object) public readonly user!: object;
  @Prop(Number) public readonly avatar!: number;

  get userPosition() {
    return this.user.position ? this.user.position : 'Не задано';
  }

  get checkUserPosition() {
    return this.user.position !== '';
  }

  get userDepartment() {
    return this.user.department ? this.user.department : 'Не задано';
  }

  get checkUserDepartment() {
    return this.user.department !== '';
  }

  get userCompany() {
    return this.user.company ? this.user.company : 'Не задано';
  }

  get checkUserCompany() {
    return this.user.company !== '';
  }

  get checkOnline() {
    return this.user.active;
  }

  get checkOffline() {
    return !this.user.active;
  }

}
</script>

<style scoped lang="scss">
  .info-user {
    padding-left: 40px;
  }
  .name-user {
    border: 1px solid rgb(71, 179, 255);
    height: 25px;
  }
  .avatar {
    width: 100px;
    height: 100px;
    background-repeat: no-repeat;
    background-size: contain;
  }
  table {
    width: 100%;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  .personal-info {
    border: 1px solid #d2d2d2;
  }
  .fontBold {
    font-weight: bold;
  }
  span {
    position: absolute;
    font-size: 20px;
    bottom: -5px;
  }
  .online {
    color: #07b622;
  }
  .offline {
    color: rgba(5, 5, 5, 0.29);
  }
</style>
