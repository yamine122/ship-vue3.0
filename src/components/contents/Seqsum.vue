<template>
<div>
	<Nav></Nav>
	<div class="seqsum">
	<div class="display"></div>
	<input v-model="first" type="text"/>
	<input v-model="second" type="text"/>
	<button @click="sum">더하기</button>
	<p>{{totalNum}}</p>
	
	</div>
</div>
</template>

<script>
import Nav from "@/components/cmm/Nav.vue"
import Footer from "@/components/cmm/Footer.vue"
export default{
	name : 'seqsum',
	components : {
		Nav,Footer
	},
	data(){
		return {
		totalNum : 0,
		first : '',
		second : ''
		}
	},
	methods : {
		sum(){
			let _first = parseInt(this.first)
			let _second = parseInt(this.second)
			let arr = [_first, _second]
			arr.sort(function(_first,_second){
				return _first - _second
			})
			let sum = 0
			let start = arr[0]
			let end = arr[1]+1
			for(let i = start; i < end; i++){
				sum += i
			}
			this.totalNum = sum
		}
		
	}
	
}
</script>
<style scoped>

</style>