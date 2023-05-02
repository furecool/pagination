<script setup>
</script>

<template>

	<ul>
		<li v-for="(item, index) in datas.slice(pageStart, pageEnd)" :key="index">
		{{ item }}
		</li>
	</ul>
	<!-- pagination -->
	<ul class="pagination">

		<li class="page-item" @click.prevent="setPage(currentPage-1)">
			<a class="page-link" href="#" aria-label="Previous">
			<span aria-hidden="true">&laquo;</span>
			</a>
		</li>

		<li class="page-item" :class="{'active': (currentPage === (n))}"
		v-for="(n, index) in totalPage" :key="index" @click.prevent="setPage(n)">
			<a class="page-link" href="#">{{ n }}</a>
		</li>

		<li class="page-item" @click.prevent="setPage(currentPage+1)">
			<a class="page-link" href="#" aria-label="Next">
			<span aria-hidden="true">&raquo;</span>
			</a>
		</li>
		
	</ul>

</template>

<script>
export default {
	data() {
		return {
			datas: [1,2,3,4,5,6,7,8,9,0,56,54634,2614,14135,65878576,967976,,0,76],//要呈現的資料
			perpage: 10, //一頁的資料數
			currentPage: 1
		};
	},
	beforeMount() {
	},
	mounted() {
	},
	computed: {
		totalPage() {
			return Math.ceil(this.datas.length / this.perpage)
			//Math.ceil()取最小整數
		},
		pageStart() {
			return (this.currentPage - 1) * this.perpage
			//取得該頁第一個值的index
		},
		pageEnd() {
			return this.currentPage * this.perpage
			//取得該頁最後一個值的index
		}
	},
	methods: {
		setPage(page) {
			if(page <= 0 || page > this.totalPage) {
				return
			}
			this.currentPage = page
		}
  },
}
</script>

<style scoped>
</style>
