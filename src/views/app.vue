<template>
    <div style="flex:1">
        <frequentContacts></frequentContacts>
    </div>
</template>

<!--引入bui-weex样式文件-->
<style lang="scss" src="bui-weex/src/css/buiweex.scss"></style>

<script>
    import frequentContacts from "./frequentContacts.vue";
    module.exports = {
        data () {
            return {}
        },
        components: {
          frequentContacts
        }
    }
</script>