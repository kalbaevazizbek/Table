<template>
  <a-layout style="border-radius: 10px">
    <a-layout-header style="line-height: 64px; width: 1665px; height: 80px; background-color: whitesmoke; border-radius: 10px;">
      <a-input-search class="ant-select-selection__placeholder" v-model="value" placeholder="Наити" :style="{ position: 'absolute', padding: '20px 30px' , width: '350px', marginLeft: '440px', color: 'white'}" enter-button  @input="closeOpacity">{{ value }}</a-input-search>
      <a-typography-title align="start" :level="3" style="padding: 20px 0; color: black">Пример</a-typography-title>
    </a-layout-header>
  </a-layout>
  <a-table :columns="columns" :data-source="data"  class="components-table-demo-nested" style="background-color: whitesmoke; border-radius: 10px; margin-top: -5px" :pagination="false">
    <template #expandedRowRender = "{ record, index }">
      <div v-if="index === 0" :pagination="false" style="background-color: whitesmoke;  height: 40px" >
        <UserOutlined style="font-size: 25px; padding: 10px 10px; background-color: blue; color: white; border-radius: 50px; cursor:pointer;" />
        <a-typography-text style="padding: 15px; font-size: 16px; font-weight: 600; margin-top: -5px; position: absolute" >Тест контактов</a-typography-text>
        <PhoneOutlined style="padding: 10px 10px; font-size: 25px; background-color: blue; color: white; border-radius: 50px; margin-left: 140px; cursor: pointer;"/>
        <MailOutlined style="padding: 10px 10px; font-size: 25px; background-color: blue; color: white; border-radius: 50px; margin-left: 10px; cursor: pointer;" />
      </div>
      <div v-if="index === 1" :pagination="false" style="background-color: whitesmoke; height: 40px" >
        <a-typography-text style="padding: 15px; font-size: 16px; font-weight: 600; margin-top: -5px; position: absolute" >Без контакта</a-typography-text>
      </div>
      <div v-if="index === 2" :pagination="false" style="background-color: whitesmoke;  height: 40px" >
        <UserOutlined style="font-size: 25px; padding: 10px 10px; background-color: blue; color: white; border-radius: 50px; cursor:pointer;" />
        <a-typography-text style="padding: 15px; font-size: 16px; font-weight: 600; margin-top: -5px; position: absolute;">Тест контактов</a-typography-text>
        <PhoneOutlined style="padding: 10px 10px; font-size: 25px; background-color: blue; color: white; border-radius: 50px; margin-left: 140px; cursor: pointer;"/>
        <MailOutlined style="padding: 10px 10px; font-size: 25px; background-color: blue; color: white; border-radius: 50px; margin-left: 10px; cursor: pointer;" />
      </div>
      <div v-if="index === 3" :pagination="false" style="background-color: whitesmoke; height: 40px" >
        <a-typography-text style="padding: 15px; font-size: 16px; font-weight: 600; margin-top: -5px; position: absolute" >Без контакта</a-typography-text>
      </div>
    </template>
  </a-table>
  <a-spin class="spin" size="large"></a-spin>
</template>
<script>
import {defineComponent} from "vue";
import { UserOutlined, PhoneOutlined, MailOutlined } from "@ant-design/icons-vue";


const columns = [
  {
    title: 'Название',
    dataIndex: 'name',
    key: 'name',
  },
  {
    title: 'Бюджет',
    dataIndex: 'byudjet',
    key: 'byudjet',
  },
  {
    title: 'Статус',
    dataIndex: 'status',
    key: 'status',
  },
  {
    title: 'Ответственный',
    dataIndex: 'otvet',
    key: 'otvet',
  },
  {
    title: 'Дата создания',
    dataIndex: 'date',
    key: 'date',
  },
];

const data = [
  {
    key: 1,
    name: 'Первая сделка',
    byudjet: '1 000',
    status: ['Принимают решение'],
    otvet: 'Андрей Соколов',
    date: '20.01.1970 17:32'
  },
  {
    key: 2,
    name: 'Сделка #31738737',
    byudjet: '0',
    status: ['Закрыто и не реализовано'],
    otvet: 'Андрей Тулев',
    date: '20.01.1970 21:54'
  },
  {
    key: 3,
    name: 'Вторая сделка',
    byudjet: '0',
    status: ['Принимают решение'],
    otvet: 'Андрей Тулев',
    date: '20.01.1970 17:32'
  },
  {
    key: 4,
    name: 'Сделка #31943981',
    byudjet: '8 888',
    status: ['Переговоры'],
    otvet: 'Андрей Тулев',
    date: '21.01.1970 00:37'
  }
];
export default defineComponent({
  components: {
    UserOutlined,
    PhoneOutlined,
    MailOutlined
  },
  data() {
    return {
      columns,
      data,
      isBlue: true,
      value: '',
    }
  },
  methods: {
    closeOpacity() {
      if (this.isBlue) {
        document.querySelector('.components-table-demo-nested').style.opacity = '0.3'
        document.querySelector('.spin').style.display = 'block'
      }
      else {
        document.querySelector('.components-table-demo-nested').style.opacity = '1'
        document.querySelector('.spin').style.display = 'none'
      }
      this.isBlue = !this.isBlue

    },
  }
})

</script>

<style scoped>
.spin {
  margin: 0 auto;
  margin-top: -140px;
  display: none;
}
</style>