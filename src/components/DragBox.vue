<script>
import draggable from 'vuedraggable';

export default {
    name: 'DragBox',
    props: ['rule', 'subRule', 'tag', 'list'],
    components: {
        draggable
    },
    render(h) {
        const subRule = this.$props.rule || {};
        let _class = '_fd-' + this.$props.tag + '-drag _fd-drag-box';
        if (!this.$children.length) {
            _class += ' ' + this.$props.tag + '-holder';
        }
        subRule.class = _class;
        const props = {...this.$props.rule, on: this.$listeners};
        if (this.$props.list) {
            props.props.list = this.$props.list;
        }
        return h(draggable, props, this.$slots.default);
    }
};
</script>