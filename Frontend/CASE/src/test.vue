<!--<template>
  <DxDataGrid
    :data-source="users"
    :show-borders="true"
    key-expr="id"
    >
    <DxPaging :default-page-size="5" />
    <DxSorting mode="multiple" />
    <DxFilterRow :visible="true" />
    <DxEditing :allow-updating="true" mode="row"/>
     
    <DxColumn data-field="id" caption="ID" :allow-editing="false"/>
    <DxColumn data-field="name" caption="Name" />
    <DxColumn data-field="email" caption="Email" />
  </DxDataGrid>

  <button class="add_user" @click="addUser">Добавить пользователя</button>
</template>

<script setup>

import { DxDataGrid, DxColumn, DxPaging, DxEditing } from 'devextreme-vue/data-grid'
import { reactive } from 'vue'

const users = reactive([
  { id: 1, name: 'Alice', email: 'alice@example.com' },
  { id: 2, name: 'Bob', email: 'bob@example.com' },
  { id: 3, name: 'Charlie', email: 'charlie@example.com' },
  { id: 4, name: 'David', email: 'david@example.com' },
  { id: 5, name: 'Eve', email: 'eve@example.com' },
  { id: 6, name: 'Frank', email: 'frank@example.com' },
]);

const user = { id: 7, name: 'Artem', email: 'sosimoishari@bigpenis.com' }


const addUser = () => {
  users.push(user)

}

</script> -->

<template>
  <DxForm :form-data="user" :col-count="2">
    <DxGroupItem caption="Контактные данные">
      <DxSimpleItem data-field="name" :validation-rules="[{ type: 'required', message: 'Имя обязательно' }]"/>
      <DxSimpleItem data-field="email" :validation-rules="[
        { type: 'required', message: 'Маил обязателен' },
        { type: 'email', message: 'Некорректный email' }
      ]" />
    </DxGroupItem>
    <DxSimpleItem data-field="isAdmin" editor-type="dxCheckBox" />
  </DxForm>
  <button class="btn" @click="rem">Сбросить</button>
</template>

<script setup>
import {
  DxForm, DxSimpleItem, DxGroupItem, DxTabbedItem
} from 'devextreme-vue/form'

import { ref } from 'vue'

const user = ref({
  name: '',
  email: '',
  phone: '',
  isAdmin: false
})

const rem = () => {
  user.value = {
  name: '',
  email: '',
  phone: '',
  isAdmin: false
}
}
</script>

<style scoped>
</style>


