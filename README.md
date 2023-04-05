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

• Arquivo cloudbuild.yaml:

	steps:
	  - name: 'gcr.io/cloud-builders/docker'
	    args: ['build', '-t', 'terraform', '.']
	  - name: 'hashicorp/terraform'
	    args: ['init']
	  - name: 'hashicorp/terraform'
	    args: ['plan']
	  - name: 'hashicorp/terraform'
	    args: ['apply', '-auto-approve']

• Arquivo main.tf:

	provider "google" {
	  project = var.project_id
	  region  = var.region
	}

	resource "google_compute_network" "network" {
	  name                    = "my-network"
	  auto_create_subnetworks = false
	}

	resource "google_compute_subnetwork" "subnetwork" {
	  name          = "my-subnetwork"
	  network       = google_compute_network.network.self_link
	  ip_cidr_range = "10.0.1.0/24"
	}

• Comandos para configurar variáveis de ambiente:

	export PROJECT_ID=<ID_DO_PROJETO>
	export REGION=<REGIAO_DESEJADA>

Comandos para implantar o pipeline de CI/CD:

	gcloud builds submit --config=cloudbuild.yaml .
