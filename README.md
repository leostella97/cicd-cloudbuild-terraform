# Pipeline de CI/CD com Cloud Buiild e Terraform no Google Cloud Plataform
<ol>
	<li>Crie um repositório no Cloud Source Repositories ou use um repositório externo (GitHub, Bitbucket, etc.).
	<li>Crie um arquivo de configuração do Cloud Build (cloudbuild.yaml) e defina os passos para construir, testar e implantar sua infraestrutura usando o Terraform.
	<li>Crie um arquivo de configuração do Terraform (main.tf) e defina sua infraestrutura como código.
	<li>Defina as variáveis de ambiente necessárias para o Cloud Build e Terraform.
	<li>Conecte seu repositório ao Cloud Build.
	<li>Configure o Cloud Build para executar o arquivo cloudbuild.yaml quando houver alterações no repositório.
	<li>Configure as permissões de serviço para o Cloud Build poder implantar no seu projeto.
	<li>Teste o pipeline de CI/CD com uma alteração no repositório.
</ol>