<template>
    <div class="pagination">
        <div class="pagination-container">
            <p>page</p>
            <button 
                ref="focused"
                class="page-button"
                v-for="(page, index) in totalPages" :key="page"
                @click="changePage(index)">{{page}}</button>
        </div>
    </div>
</template>

<script>
export default {
    props: ['totalPages', 'pageLoaded'],
    mounted() {
       let button = this.$refs.focused[this.pageLoaded];
        button.focus();
    },
    data() {
        return {
            active: true,
            activeEl: this.pageLoaded
        }
    },
    methods: {
        changePage(index) {
            this.$emit('pageChange', index)
        }
    }
}
</script>

<style scoped>
.pagination {
    width: 100%;
    position: fixed;
    bottom: 0;
    padding:0;
    background: #fff;
    border:1px solid #cccc;
}
.pagination-container {
    display: flex;
    align-items: center;
    justify-content: center;
}
.page-button {
    border: none;
    padding: .5em 1em;
    background: blue;
    color: white;
    margin: 0 1em 0;
    
}
</style>