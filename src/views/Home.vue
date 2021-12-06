

<script>
import PropsChild from "../components/PropsChild.vue";

export default {
  name: "Home",
  components: {
    PropsChild,
  },
  render() {
    return (
      <div>
        <h1>根本就没有产品经理，或者人人都是产品经理</h1>
        <props-child parent-name="并不是顶着产品经理的头衔才是产品经理，而是那些在定义产品、做产品决策的人，才是真正的产品经理" />
      </div>
    );
  },
};
</script>
