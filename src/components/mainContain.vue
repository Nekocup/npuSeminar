<template>
  <div class="container">
    <div class="section1">
      <img src="@/assets/image/banner.svg" alt="" />
    </div>
    <div class="section2">
      <h1>註冊您的帳號</h1>
      <form @submit.prevent="register()">
        <div class="name">
          <input
            type="text"
            name="firstName"
            id="firstName"
            placeholder="姓氏"
            v-model="firstName"
          />
          <input
            type="text"
            name="lastName"
            id="lastName"
            placeholder="名字"
            v-model="lastName"
          />
        </div>
        <div>
          <input
            type="email"
            name="email"
            id="email"
            placeholder="信箱"
            v-model="email"
          />
          <input
            type="password"
            name="password"
            id="password"
            placeholder="密碼"
            v-model="password"
          />
          <input
            type="text"
            name="school"
            id="school"
            placeholder="所屬機關 ( 學校 )"
            v-model="school"
          />
          <input
            type="text"
            name="dept"
            id="dept"
            placeholder="所屬單位 ( 系名 )"
            v-model="dept"
          />
          <input
            type="text"
            name="phone"
            id="phone"
            placeholder="連絡電話"
            v-model="phone"
          />
        </div>
        <div class="join">
          <div>
            <span>是否參加團體參觀行程 ?</span>
            <div class="option">
              <span>是 </span>
              <input
                type="radio"
                name="groupVisit"
                value="1"
                v-model="groupVisit"
              />
              <span>否 </span>
              <input
                type="radio"
                name="groupVisit"
                value="0"
                v-model="groupVisit"
              />
            </div>
          </div>
          <div>
            <span>是否參加歡迎晚宴 ?</span>
            <div class="option">
              <span>是 </span>
              <input
                type="radio"
                name="toDinner"
                value="1"
                v-model="toDinner"
              />
              <span>否 </span>
              <input
                type="radio"
                name="toDinner"
                value="0"
                v-model="toDinner"
              />
            </div>
          </div>
        </div>
        <input type="submit" value="註冊" id="buttonCss" />
      </form>
    </div>
    <div class="backgroundRight"></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      firstName: "",
      lastName: "",
      email: "",
      password: "",
      school: "",
      dept: "",
      phone: "",
      toDinner: 0,
      groupVisit: 0,
    };
  },
  methods: {
    register() {
      if (
        this.firstName == "" ||
        this.lastName == "" ||
        this.password == "" ||
        this.school == "" ||
        this.dept == "" ||
        this.phone == ""
      ) {
        setTimeout(() => {
          alert("全部都要填寫，不得為空 !!");
        }, 0);
        return;
      }
      if (this.password.length < 8) {
        setTimeout(() => {
          alert("密碼長度最少8碼 !!");
        }, 0);
        return;
      }
      const axios = require("axios");

      axios
        .post("/register", {
          firstName: this.firstName,
          lastName: this.lastName,
          password: this.password,
          school: this.school,
          dept: this.dept,
          phone: this.phone,
          email: this.email,
          toDinner: this.toDinner,
          groupVisit: this.groupVisit,
        })
        .then((data) => {
          if (data.data == "success") {
            setTimeout(() => {
              alert("註冊成功 !");
              window.location.href = "https://itaoi2022.npu.edu.tw/index.html";
            }, 0);
          } else if (data.data == "email same") {
            alert("信箱已被註冊過!");
          } else {
            alert("註冊失敗");
          }
        });
    },
  },
};
</script>
<style lang="scss"></style>
