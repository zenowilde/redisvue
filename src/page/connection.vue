<template>
    <div>
        <el-menu-item v-bind:index="indexa">
            <i class="el-icon-s-platform"></i>
            {{ name }}
            <el-button size="mini" v-show="statue"  @click="closeConnection" circle>关闭</el-button>
            <el-button size="mini" v-show="!statue" @click="openConnection" circle>打开</el-button>
            <el-button size="mini"  @click="editConnection" circle>编辑</el-button>
            <el-button size="mini"  @click="removeConnection" circle>删除</el-button>
        </el-menu-item>
    </div>
</template>

<script>
import { name } from 'file-loader';

export default {
    props: [
        "indexa",
        "id",
        "name",
        "host",
        "port",
        "username",
        "password"
    ],
    data() {
        return {
            statue: false
        }   
    },
    methods: {
        removeConnection() {
            this.$emit('removeConnection', this.id)
        },

        closeConnection() {
            console.log("close" + id + name);
            this.statue = false;
        },

        openConnection() {
            console.log("open" + id + name);
            this.statue = false;
        },
        editConnection() {

        }
    }
}


</script>

<style>

</style>