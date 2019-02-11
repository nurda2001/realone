<template>
	<div>
		<v-navigation-drawer  absolute temporary v-model="drawer" class="hidden-md-and-up">
		<v-list>
			<v-list-tile v-for="(item,i) in menuItems" :key="`navdrawer${i}`">
				<v-list-tile-action>
					<v-icon v-html="item.icon"></v-icon>
				</v-list-tile-action>
				<v-list-tile-content>
						<v-list-tile-title v-text="item.title"></v-list-tile-title>
					</v-list-tile-content>
			</v-list-tile>
		</v-list>
		</v-navigation-drawer>
		<v-toolbar v-if="show"  app  color="white">
			<v-toolbar-side-icon class="hidden-md-and-up" @click.stop="drawer = !drawer"></v-toolbar-side-icon>
			<router-link to="/" tag="span" style=" cursor: pointer">
			<v-toolbar-title v-text="'English In Aktau'"></v-toolbar-title>
		</router-link>
			<v-spacer></v-spacer>
			<v-toolbar-items class="hidden-sm-and-down">
				<v-btn v-for="(item, i) in menuItems" flat :key="`menuItem${i}`" :to="item.route" >
					<v-icon left v-html="item.icon"></v-icon>
					{{item.title}}
				</v-btn>
				<v-btn>Hi</v-btn>
			</v-toolbar-items>
		</v-toolbar>
	</div>	
</template>

<script>
	export default{
		data(){
			return{
				drawer: false,
				show: true
			}
		},
		computed:{
			menuItems(){
				return[
                       {
                       	icon: 'visibility', title: 'Read', route: '/books'
                       },
                         {
                       	icon: 'extension',
                       	title: 'Learn a new word',
                       	route: '/words'
                       },
                         {
                       	icon: 'account_circle',
                       	title: 'My Profile',
                       	route: '/profile'
                       },
                         {
                       	icon: 'exit_to_app',
                       	title: 'Exit',
                       	route: '/logout'
                       },
                         {
                       	icon: 'input',
                       	title: 'Sign In',
                       	route: '/signin'
                       },
                         {
                       	icon: 'lock_open',
                       	title: 'Regestration',
                       	route: '/signup'
                       }
				]
			}
		}
	}
</script>

<style scoped>
	v-btn{
		text-decoration-style: none;
	}
</style>