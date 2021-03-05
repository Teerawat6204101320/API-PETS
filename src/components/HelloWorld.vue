<template>
  <div class="hello">
    <h1>API <span>PETS</span></h1>
    <table class="content-table">
      <tr class="thead">
        <td>ID</td>
        <td>Name</td>
        <td>Phone</td>
        <td>Email</td>
      </tr>
      <tr v-for="items in mydata.partners" :key="items.id" class="thead-data">
        <td>{{ items.id }}</td>
        <td>{{ items.name }}</td>
        <td>{{ items.phone1 }}</td>
        <td>{{ items.url }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  props: {},
  data() {
    return {
      mydata: {},
    };
  },

  mounted() {
    axios({
      method: "GET",
      url: "https://animais-de-rua.p.rapidapi.com/partners",
      headers: {
        "x-rapidapi-key": "44bb268c47msh8ed594fedc15d99p1f76cajsnb84b15fa4047",
        "x-rapidapi-host": "animais-de-rua.p.rapidapi.com",
      },
    }).then((total) => {
      this.mydata = total.data;
      console.log(total);
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=RocknRoll+One&display=swap");

.hello {
  font-family: "RocknRoll One", sans-serif;
}
.content-table {
  border-collapse: collapse;
  margin: 25px 0;
  border-radius: 5px 5px 0 0;
  overflow: hidden;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
}
.content-table .thead {
  background: #009876;
  color: #ffffff;
  font-weight: bold;
}
.content-table td {
  padding: 15px 25px;
  text-align: left;
}
.thead-data {
  border-bottom: 1px solid #dddddd;
}
.thead-data:nth-of-type(even) {
  background-color: #f3f3f3;
}
.thead-data:last-of-type {
  border-bottom: 2px solid #009879;
}
table {
  position: absolute;
  left: 50%;
  top: 20%;
  transform: translate(-50%);
  width: 80%;
}
@media only screen and (max-width: 768px) {
  table {
    width: 600px;
  }
  .content-table {
    font-size: 13px;
  }
}
@media only screen and (max-width: 590px) {
  table {
    width: 10%;
  }
  .content-table {
    font-size: 10px;
  }
  h1 {
    font-size: 25px;
  }
  .content-table td {
    padding: 5px 13px;
    text-align: left;
  }
}
</style>
