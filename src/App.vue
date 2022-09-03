<template>
  <div>
    <div class="text-center" id="slogan">
      <h1>Projeto Vue</h1>
      <h6 class="text-secondary">Gerador de nomes utilizando Vue.js, GraphQL e Node.</h6>
    </div>
    <div id="main">
      <DomainList />
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
import DomainList from "./components/DomainList.vue";

export default {
	name: "App",
	components: {
		DomainList,
	},
	computed: {
		domains() {
			const domains = [];

			for (const prefix of this.prefixes) {
				for (const sufix of this.sufixes) {
					const name = prefix + sufix;
					const url = name.toLowerCase();
					const checkout = `https://checkout.hostgator.com.br/?a=add&sld=${url}&tld=.com.br`;
					
					domains.push({
						name,
						checkout,
					});
				}
			}

			return domains;
		}
	},
};
</script>

<style>
#slogan {
  margin-top: 30px;
  margin-bottom: 30px;
}
#main {
  background-color: #f1f1f1;
  padding-top: 30px;
  padding-bottom: 30px;
}
</style>
