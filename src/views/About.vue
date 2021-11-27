<template>
  <div class="about">
    <h1>相关按钮</h1>
    <p>请注意，这是在该页面中局部使用ALert，不影响在main.js中使用Element</p>
    <p>局部使用一定要引入相关模块：import VueSimpleAlert from "vue-simple-alert"</p>
<div id="app">
    <header id="header">
      <div id="logo">
        <!-- <img id="logo-image" alt="Vue logo" src="./assets/logo.png" /> -->
      </div>
      <div id="title">
      </div>
    </header>
    <h2>Alert 例子</h2>
    <p>请注意，存在一点Bug，ALert中的取消键捕获困难，建议使用confirm</p>
    <div id="examples">
      <div id="alert-example">
        <button type="button" @click="alertExample0">普通的Alert</button>
        <button
          type="button"
          class="swal2-confirm swal2-styled"
          @click="alertExample2"
        >
          带有标题的Alert
        </button>
        <button
          type="button"
          class="swal2-confirm swal2-styled"
          @click="alertExample3"
        >
          成功Alert
        </button>
        <button
          type="button"
          class="swal2-confirm swal2-styled"
          @click="alertExample4"
        >
          警告Alert(中文版本的回复)
        </button>
      </div>

      <br />
      <h2>Confirm examples</h2>
      <div id="confirm-example">
        <button type="button" @click="confirmExample0">Normal Confirm</button>
        <el-button
          type="success"
          class="swal2-confirm swal2-styled"
          @click="confirmExample1"
        >
          简单confirm
        </el-button>
        <el-button
          type="dark"
          @click="confirmExample2"
        >
          问题confirm
        </el-button>
        <el-button
          type="danger"
          @click="confirmExample3"
        >
          删除键confirm (中文版本)
        </el-button>
      </div>

      <br />
      <h2>Prompt 例子</h2>
      <div id="prompt-example">
        <el-button type="warning" plain @click="promptExample0">正常的Prompt</el-button>
        <el-button type="success" plain
          @click="promptExample1"
        >
          简单的Prompt
        </el-button>
        <el-button type="danger" 
          plain
          @click="promptExample2"
        >
          问题icon
        </el-button>
        <el-button type="primary"
           plain
          @click="promptExample3"
        >
          邮件Prompt
        </el-button>
      </div>

      <br />
      <h2>Advanced 例子</h2>
      <div id="advanced-example">
        <button
          type="button"
          class="swal2-confirm swal2-styled"
          @click="advancedExample1"
        >
          震动的
        </button>
        <button
          type="button"
          class="swal2-confirm swal2-styled"
          @click="advancedExample2"
        >
          测试
        </button>
        <button
          type="button"
          class="swal2-confirm swal2-styled"
          @click="advancedExample3"
        >
          测试
        </button>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
//局部使用一定要引入相关模块
import VueSimpleAlert from "vue-simple-alert";

export default {
  methods:{
    alertExample4() {
    VueSimpleAlert.alert(
      "警告你不要碰我",
      "110",
      "warning",
    {   showCancelButton: true,
        confirmButtonText: "确认",
        cancelButtonText: "取消",
      }
    ).then(() => console.log("关闭"));
  },
    alertExample0() {
    window.alert("谈恋爱应该处处让着男朋友，让他做饭，让他洗碗，让他洗衣服，让他赚钱。");
  },
  alertExample1() {
    VueSimpleAlert.alert("当代青年主要运动项目：取快递、取外卖！").then(() =>
      console.log("Closed")
    );
  },
  alertExample2() {
    VueSimpleAlert.alert("步入社会后，我才发现，我拼不了爹妈，只能拼多多。", "拼多多").then(
      () => console.log("Closed")
    );
  },
  alertExample3() {
    VueSimpleAlert.alert(
      "女人要么美一点，要么努力一点，如果又美又努力，那就可以拽一点。",
      "呵，女人！",
      "success"
    ).then(() => console.log("Closed"));
  },
  confirmExample0() {
    window.confirm("让我坚持下去的，不是什么宏大的理想，而是赚好多好多钱，然后买买买。");
  },
  confirmExample1() {
    VueSimpleAlert.confirm("秀恩爱的人换了一波儿又一波儿，只有我，雷打不动地单身。", "Confirm");
  },
  confirmExample2() {
    VueSimpleAlert.confirm(
      "有人说我长得帅，我笑了，因为我笑起来更帅。",
      "有人说我长得帅？",
      "question"
    )
      .then((r) => {
        console.log(r);
      })
      .catch(() => {
        console.log("OK not selected.");
      });
  },
  confirmExample3() {
    VueSimpleAlert.confirm("男人喜欢漂亮脸蛋，女人喜欢甜言蜜语。所以女人化妆，男人撒谎。", "漂亮脸蛋", "error",
      {
        showCancelButton: true,
        confirmButtonText: "确认",
        cancelButtonText: "取消",
      }
    ).then(() => {
        VueSimpleAlert.alert(
        "我想安安心心干事不想被导师控制干杂活了",
        "难",
        "success",
        {
        confirmButtonText: "好的",
        })
      })
      .catch(() => {
        this.alertExample3();
        console.log("取消");
        //取消
      });
  },

  promptExample0() {
    window.alert(window.prompt("输入你的名字", "Dongliang Chen"));
  },
  promptExample1() {
    VueSimpleAlert.prompt("输入你的名字", "Dongliang Chen").then((r) => {
      if (r) VueSimpleAlert.alert(r, "你的名字:", "success");
    });
  },
  promptExample2() {
    VueSimpleAlert.prompt("输入你的名字", "Dongliang Chen", "例子", "question")
      .then((r) => {
        VueSimpleAlert.alert(r, "你的名字:", "success");
      })
      .catch(() => console.log("canceled"));
  },
  promptExample3() {
    VueSimpleAlert.prompt(
      "输入你的email",
      "someone@example.com",
      "例子",
      "question",
      { input: "email" }
    )
      .then((r) => {
        VueSimpleAlert.alert(r, "你的email:", "success");
      })
      .catch(() => console.log("canceled"));
  },

  advancedExample1() {
    const options = {
      title: "<strong>请你</strong> &nbsp; 吃饭",
      text: "如果哪一天你突然想起我，请拿起手机拨通我的号码，哪怕我再忙再没空，只要你一句“我请你吃饭”",
      footer: "<a href=''>我都会风雨无阻的出现在你的面前。</a>",
      type: "success",
      showCancelButton: true,
      confirmButtonText: "<i class='fa fa-thumbs-up'></i> 好吧!",
      cancelButtonText: "不要",
      reverseButtons: true,
      timer: 3000,
      width: 500,
      animation: true,
      customClass: {
        popup: "animated tada"
      },
      padding: "3em",
      background: "#FFFFE0",
      backdrop: `
        rgba(200,0,0,0.3)
        center left
        no-repeat
      `
    };

    VueSimpleAlert.fire(options).then(() => {
      if (r.value) {VueSimpleAlert.alert(r.value, "Result")}
      else{
            console.log("这是我对朋友一生一世的承诺！")
      };
    });
  },
  advancedExample2() {
    VueSimpleAlert.alert(
      "喜欢一个人就要去表白，不用管那么多，虽然失败的可能性很大，但是万一成了备胎呢？",
      "表白",
      "success",
      {
        confirmButtonText: "知道了!"
      }
    );
  },
  advancedExample3() {
    VueSimpleAlert.confirm("众里寻她千百度，踏平脚下路。", "蓦然回首", "error", {
      reverseButtons: true
    })
      .then((r) => {
        console.log(r);
      })
      .catch(() => {
        console.log("OK not selected.");
      });
  }
  },
}
</script>



