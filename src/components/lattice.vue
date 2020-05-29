
<script lang="tsx">
import { Component, Prop, Vue } from "vue-property-decorator";
import { CreateElement } from "vue";

@Component
export default class HelloWorld extends Vue {
  // @Prop() 类似 props: { msg: { type: Number }, propB: { default: 'default value' },  }
  // @Prop({ default: "default value" }) readonly propB!: string;

  protected state = {
    status: ""
  };

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
  width: 50vw;
  height: 50vh;
  margin: auto;
  .start {
    text-align: center;
  }
}
</style>