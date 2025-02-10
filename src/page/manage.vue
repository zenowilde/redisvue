<template>
	<div class="manage_page fillcontain">
		<el-row style="height: 100%;">
	  		<el-col :span="4"  style="min-height: 100%; background-color: #324057;">
				<el-menu :default-active="defaultActive" style="min-height: 100%;" theme="dark" router>
                    <el-menu-item index="/"><i class="el-icon-menu"></i>首页</el-menu-item>
					<el-submenu index="2">
						<template slot="title"><i class="el-icon-document"></i>连接管理</template>
						<el-menu-item @click="showAddConnDialog"><i class="el-icon-plus"></i>添加连接</el-menu-item>
                        <connection v-for="(item, i) in connections" v-bind="item" :key="item.id" :indexa="2 + i + ''"></connection>
					</el-submenu>
				</el-menu>
			</el-col>
			<el-col :span="20" style="height: 100%;overflow: auto;">
				<keep-alive>
				    <router-view></router-view>
				</keep-alive>
			</el-col>
		</el-row>
        <el-dialog title="添加连接" v-model="showAddConn">
                <el-form :model="connection">
                    <el-form-item label="连接名" label-width="100px">
                        <el-input v-model="connection.name" auto-complete="off"></el-input>
                    </el-form-item>
                    <el-form-item label="主机" label-width="100px">
                        <el-input v-model="connection.host" auto-complete="off"></el-input>
                    </el-form-item>
                    <el-form-item label="端口" label-width="100px">
                        <el-input v-model="connection.port" auto-complete="off"></el-input>
                    </el-form-item>
                    <el-form-item label="用户名" label-width="100px">
                        <el-input v-model="connection.username" auto-complete="off"></el-input>
                    </el-form-item>
                    <el-form-item label="密码" label-width="100px">
                        <el-input v-model="connection.password" auto-complete="off"></el-input>
                    </el-form-item>
                </el-form>
              <div slot="footer" class="dialog-footer">
                <el-button @click="showAddConn = false">取 消</el-button>
                <el-button type="primary" @click="addConnection">确 定</el-button>
              </div>
            </el-dialog>
  	</div>
</template>

<script>
    import Connection from './connection.vue';

    export default {
		computed: {
			defaultActive: function(){
				return this.$route.path.replace('/', '');
			}
		},

        data() {
            return {
                connections: [
                    
                ],
                connection: {},
                showAddConn: false
            }
        },

        components: {
    		Connection,
    	},


        methods: {
            addConnection() {
                this.connections.push(this.connection);
                this.connection = {};
                this.showAddConn = false;
            },
            showAddConnDialog() {
                this.showAddConn = true;
            }
        }
    }
</script>


<style lang="less" scoped>
	@import '../style/mixin';
	.manage_page{
		
	}
</style>
