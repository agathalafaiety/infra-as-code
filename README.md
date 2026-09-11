# Infra as Code

Projeto de estudos sobre Infraestrutura como Código (IaC) usando Terraform, AWS e GitHub Actions.

O exemplo provisiona um bucket Amazon S3 configurado para hospedagem de site estático na região `us-east-1`.

## Tecnologias

- Terraform
- Amazon Web Services (AWS)
- Amazon S3
- GitHub Actions

## Estrutura

```text
infra-as-code/
├── .github/workflows/
│   └── provision-s3-static-site.yaml
└── terraform/
    └── s3-bucket-static/
        └── main.tf
```

## Execução local

Configure suas credenciais da AWS e acesse a pasta do Terraform:

```bash
cd terraform/s3-bucket-static
```

Inicialize e revise o plano:

```bash
terraform init
terraform plan -var="bucket_name=meu-site"
```

Crie os recursos:

```bash
terraform apply -var="bucket_name=meu-site"
```

Para remover os recursos criados:

```bash
terraform destroy -var="bucket_name=meu-site"
```

## GitHub Actions

O workflow é iniciado quando uma nova issue é aberta. O título da issue é utilizado para compor o nome do bucket.

Para executar a automação, configure os seguintes secrets no GitHub:

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `GH_TOKEN`

> Atenção: o exemplo desativa os bloqueios de acesso público do bucket. Utilize apenas em ambientes de estudo e revise as permissões antes de usar em produção.

Desenvolvido por [Agatha Lafaiety](https://github.com/agathalafaiety).
