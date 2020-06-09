
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
      <div class="box">
        <div class="start">Game Start</div>
        <div>{messageCount}</div>
        <button onclick={increment}>++++</button>
        <button onclick={decrement}>-----</button>

        <div></div>
      </div>
    );
  }
}
</script>

<style scoped lang="less">
.box {
  border: 2px solid #ddd;
  width: 50vw;
  height: 50vh;
  margin: auto;
  .start {
    text-align: center;
  }
}
</style>