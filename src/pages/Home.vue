<template>
  <div class="box">
    <h2 class="logo">TODO</h2>
    <button @click="decrement">-</button>
    {{messageCount}}
    <button @click="increment">+</button>

    <el-tree
      :data="dataJson"
      node-key="id"
      default-expand-all
      draggable
      :allow-drop="allowDrop"
      :allow-drag="allowDrag"
    ></el-tree>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

const data = [
  {
    id: 1,
    label: "一级 1",
    children: [
      {
        id: 4,
        label: "二级 1-1",
        children: [
          {
            id: 9,
            label: "三级 1-1-1"
          },
          {
            id: 10,
            label: "三级 1-1-2"
          }
        ]
      }
    ]
  },
  {
    id: 2,
    label: "一级 2",
    children: [
      {
        id: 5,
        label: "二级 2-1"
      },
      {
        id: 6,
        label: "二级 2-2"
      }
    ]
  },
  {
    id: 3,
    label: "一级 3",
    children: [
      {
        id: 7,
        label: "二级 3-1"
      },
      {
        id: 8,
        label: "二级 3-2",
        children: [
          {
            id: 11,
            label: "三级 3-2-1"
          },
          {
            id: 12,
            label: "三级 3-2-2"
          },
          {
            id: 13,
            label: "三级 3-2-3"
          }
        ]
      }
    ]
  }
];

const dataJson = [
  {
    Cmd: "bootPuppeteer",
    Comment: "启动爬虫程序",
    Options: {
      headless: false,
      args: ["--no-sandbox"],
      defaultViewport: null
    }
  },
  {
    Cmd: "newPage",
    Comment: "创建页面"
  },
  {
    Cmd: "navigation",
    Comment: "在浏览器打开链接",
    Key: "url",
    ScreenshotBefore: false,
    ScreenshotBehind: false,
    ScreenshotFull: false
  },
  {
    Cmd: "try",
    Comment: "包裹要尝试的语句 并在出现异常时捕获获取的错误",
    Key: "momo",
    Json: [
      {
        Cmd: "newPage",
        Comment: "创建页面"
      }
    ],
    ScreenshotBefore: false,
    ScreenshotBehind: false,
    ScreenshotFull: false
  },
  {
    Cmd: "closePage",
    Comment: "关闭页面"
  },
  {
    Cmd: "shutdown",
    Comment: "关闭浏览器"
  }
];

@Component
export default class HelloWorld extends Vue {
  // @Prop() 类似 props: { msg: { type: Number }, propB: { default: 'default value' },  }
  @Prop() private msg!: string;
  @Prop({ default: "default value" }) readonly propB!: string;

  protected count: number = 0;
  protected data: {}[] = data;
  protected dataJson: any = dataJson;
  protected idCount: number = 0;

  private created(): void {
    console.log("组件创建好了");
    this.dataJson = this.addId(this.dataJson);
    console.log(dataJson);
  }

  get messageCount(): string {
    return "现在的数字" + this.count;
  }

  increment() {
    this.count++;
  }

  decrement() {
    this.count--;
  }

  addId(data: any): any {
    // id层级
    this.idCount++;

    // 创建id随机数
    let random = Math.floor(Math.random() * 10 + 1);

    data.forEach((p: any, idx: number, newAry: any) => {
      if (p.hasOwnProperty("Json")) {
        p["id"] = this.idCount + "" + idx + random;
        p["label"] = p.Comment;
        this.addId(p["Json"]);
        return data;
      }
      p["label"] = p.Comment;
      p["id"] = this.idCount + "" + idx + random;
    });

    return data;
  }

  allowDrop(draggingNode: any, dropNode: any, type: any) {
    return true;
  }
  allowDrag(draggingNode: any) {
    return true;
  }
}
</script>

<style scoped lang="less">
.box {
  .logo {
    font-size: 60px;
    margin: 100px 0;
    text-align: center;
  }
}

/deep/ .el-table .warning-row {
  background: oldlace;
}

/deep/ .el-table .success-row {
  background: #f0f9eb;
}
</style>