<template>
	<div>
		我是子组件
		<button @click="call">打电话给父组件</button><hr/>
<!--		{{'我是sub' | myFilter}}-->
	</div>
</template>

<script>
    // 引入连接器
    import connector from "../../connector.js";
    export default {
        name: "Sub",
        data() {
            return {
            
            }
        },
        methods: {
            call() {
                // 发射信号
	            connector.$emit('phone', '62分钟来')
            }
        }

    }
</script>

<style scoped>
    div {
	    background-color: cyan;
	    font-size: 2rem;
    }
</style>