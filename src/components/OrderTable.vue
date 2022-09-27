<script>
import { ref } from "vue";
export default {
  setup() {
    let coffeeList = ref([
      {
        name: "咖啡",
        price: 100,
        size: "S",
        notes: "這裡可以填寫備註",
      },
    ]);
    function create() {
      coffeeList.value.push({
        name: "咖啡",
        price: 0,
        size: "S",
        notes: "",
      });
    }
    function deleteByIndex(index) {
      coffeeList.value.splice(index, 1);
    }
    return {
      coffeeList,
      create,
      deleteByIndex,
    };
  },
};
</script>

<template>
  <main>
    <button @click="create()" style="margin: 2vh 0">新增品項</button>

    <table>
      <thead>
        <tr>
          <th>品項名稱</th>
          <th>價格</th>
          <th>尺寸(L/M/S)</th>
          <th>備註</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(coffee, index) in coffeeList" :key="coffee">
          <td contenteditable="true">
            {{ coffee.name }}
          </td>
          <td contenteditable="true">
            {{ coffee.price }}
          </td>
          <td contenteditable="true">
            {{ coffee.size }}
          </td>
          <td contenteditable="true">
            {{ coffee.notes }}
          </td>
          <td>
            <button @click="deleteByIndex(index)" style="white-space: nowrap">
              刪除
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </main>
</template>

<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  align-items: center;
  table {
    background-color: rgb(33, 33, 33);
    color: rgba(255, 255, 255, 0.87);
    width: 60%;
    tr {
      border-bottom-color: rgba(255, 255, 255, 0.12);
      th,
      td {
        padding: 5px;
      }
      th {
        text-align: start;
        &:first-of-type {
          width: 10vw;
        }
        &:nth-of-type(2) {
          width: 5vw;
        }
        &:nth-of-type(3) {
          width: 7vw;
        }
        &:nth-of-type(4) {
          width: 30vw;
        }
      }
      td {
        word-break: break-all;
      }
    }
  }
  @media (max-width: 575.98px) {
    table {
      width: 100%;
      tr {
        th {
          &:first-of-type {
            width: 22vw;
          }
          &:nth-of-type(2) {
            width: 10vw;
          }
          &:nth-of-type(3) {
            width: 10vw;
          }
          &:nth-of-type(4) {
            width: 45vw;
          }
        }
      }
    }
  }
}
</style>
