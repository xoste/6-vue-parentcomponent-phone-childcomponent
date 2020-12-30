<template>
	<!--<div>
		<Sub></Sub>
		<button @click="listen">父组件焦急的听电话</button><hr/>
		请输入内容：
		<input type="text" name="" v-model="text"/>
		显示内容：{{text | myFilter}}<hr/>
	</div><hr/>-->
	<div>
		<Sub ref="sub"></Sub>
		<div ref="myDiv">
			{{text}}
		</div>
	</div>
</template>

<script>
	// 引入连接器
	import connector from "../connector";
	import Sub from "./views/Sub";
	
    export default {
        data() {
            return {
                text:'123'
            }
        },
        methods: {
            listen() {
                connector.$on('phone', function (msg) {
                    console.log(msg);
                })
            }
        },
        /*filters: {
            myFilter(value) { // value--> text
                // 将输入的内容做一个反转
	            // 转换成数组，反转数组，转换成字符串
                return value.split('').reverse().join('');
            }
        },*/
	    components: {
            Sub:Sub
	    },
	    /**
	     * 组件创建后，数据已经完成初始化， 但是DOM还未生成
	     * */
	    // 时间的处理函数（created）
	    created() {
	       console.log('created:', this.$refs.myDiv);
        }, // 数据装载后，各种数据已经就位，将数据渲染到DOM上DOM已经生成
	    mounted() {
	        console.log("mounted:", this.$refs.myDiv);
	        console.log('sub:', this.$refs.sub.$el);
	        this.$refs.myDiv.innerHTML = '哈哈哈';
	        this.$refs.sub.$el.innerHTML = '嘻嘻嘻';
	        // 涉及DOM类的操作
		    // this.$refs.myDiv.innerHTML === '哈哈哈';
            // 涉及到数据的操作
		    this.text = '哈哈哈';
        }
    }
</script>