
<script lang="tsx">
import { Component, Prop, Vue } from "vue-property-decorator";
import { CreateElement } from "vue";

@Component
export default class HelloWorld extends Vue {
  // @Prop() 类似 props: { msg: { type: Number }, propB: { default: 'default value' },  }
  // @Prop({ default: "default value" }) readonly propB!: string;

  protected count: number = 0;

  protected idCount: number = 0;

  private created(): void {
    console.log("组件创建好了");
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

  // jsx
  render(h: CreateElement) {
    const { decrement, messageCount, increment } = this;

    return (
      <div>
        <button onclick={decrement}>-</button>
        <div>12346 {messageCount}</div>
        <button onclick={increment}>+</button>
      </div>
    );
  }

  // 输入：["h","e","l","l","o"]
  // 输出：["o","l","l","e","h"]
  reverse(ary: any): any {
    let length: number = ary.length;

    return ary;
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