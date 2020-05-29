
<script lang="tsx">
import { Component, Prop, Vue } from "vue-property-decorator";
import { CreateElement } from "vue";

interface state {
  id: String;
  row: Number;
  column: Number;
  opened: Boolean;
  flagged: Boolean;
  mined: Boolean;
  neighborMineCount: Number;
}

@Component
export default class HelloWorld extends Vue {
  // @Prop() 类似 props: { msg: { type: Number }, propB: { default: 'default value' },  }
  // @Prop({ default: "default value" }) readonly propB!: string;

  protected state!: state;

  private created(): void {
    console.log("组件创建好了");
  }

  // jsx
  render(h: CreateElement) {
    return <div class="box"></div>;
  }
}
</script>

<style scoped lang="less">
.box {
  border: 2px solid #ddd;
  width: 15px;
  height: 15px;
  background-color: #fff;
  cursor: pointer;
  &:hover {
    background-color: azure;
  }
}
</style>