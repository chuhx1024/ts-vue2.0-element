<template>
    <div id="app">
        <h1 class="main-title">你好</h1>
        <el-row>
            <el-button>默认按钮</el-button>
            <el-button type="primary">主要按钮</el-button>
            <el-button type="success">成功按钮</el-button>
            <el-button type="info">信息按钮</el-button>
            <el-button type="warning">警告按钮</el-button>
            <el-button type="danger">危险按钮</el-button>
        </el-row>
        <router-view/>
    </div>
</template>

<style lang="scss" scoped>
.main-title {
    color: $primary-color;
}

</style>
