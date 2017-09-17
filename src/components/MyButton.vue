<template>
    <div>
        <div slot="body">{{showDate}}</div>
        <button type="button" class="btn btn-danger " @click="toggle1">去父组件</button>
    </div>
</template>
<script>
export default {
    props: ["showDate"],
    methods: {
        toggle1() {
            this.$emit('toggleEvent', "false")
        }
    }

}
</script>
