<template>
  <div>
    <ul>
      <li v-for="user in users" v-bind:key="user.id">{{ user }}</li>
    </ul>  
  </div>
</template>

<script lang="ts">
import {Vue, Component, Inject} from 'vue-property-decorator'
import { AxiosStatic } from 'axios';
// import UserService, { User } from '@/services/UserService';
import  {IUserService,  User } from '@/services/UserService';
// import axios from 'axios'



@Component
export default class InjectTest extends Vue {
  users: User[] = []
  
  // 어디선가 myHttp에다가 axios를 주입할수 있도록 ...
  // inject 할꺼니깐 느낌표 .. 
  // @Inject() myHttp!: AxiosStatic;
  @Inject() userService!: IUserService

  async create() {
    // const res = await axios.get('https://api.github.com/users')
    // console.log(res.data)
    // const res = await this.myHttp.get('https://api.github.com/users')
    // this.users = res.data

    this.users = await this.userService.getUsers()
  }
}
</script>
