
# Documentação Dataform CLI

Nessa documentação será descrito um passo a passo de como utilizar e criar seu primeiro projeto via dataform CLI.

## 1. Ativação das APIs no Google CLoud Plataform

- 1.1 Na aba de MarketPlace do GCP, digitar no campo de pesquisa "BigQuery", e ativar a API.

![alt text](/imgs/image.png)

- 1.2 Na aba de MarketPlace do GCP, digitar no campo de pesquisa "Dataform", e ativar a API.

![alt text](/imgs/image-1.png)

## 2. Criar uma conta de serviço

- 2.1 Acessar o ambiente de IAM e Administrador acessar a aba "Contas de serviço".

![alt text](/imgs/image-2.png)

- 2.2 Clicar em **Criar uma conta de serviço** e inserir o nome de sua preferência.

![alt text](/imgs/image-3.png)

Ao clicar em concluir, ele irá baixa um JSON com as credenciais da sua conta de serviço.

## ⚠️ATENÇÃO⚠️

**Esse JSON contém dados sensiveis que disponibilizam acesso a sua conta Google, não compartilhe essas informações com ninguém e as mantenha em algum local seguro e controlado.**

## 3. Conceder papéis para sua conta de serviço

- 3.1 Na aba IAM em **permissões** você verá listado todos os principais usuários do seu projeto GCP, caso você não possua acesso, solicitar ao seu gestor para conceder a sua conta de serviço os devidos acessos, sendo eles:

- Editor de dados BigQuery
- Editor do Dataform
- Usuário de jobs do BigQuery

- 3.2 Concedendo os acessos, clique no botão "Permitir Acesso", e preencha o formulário de acordo com os dados da sua conta de serviço:

![alt text](/imgs/image-4.png)

## 4. Configurar ambiente local

- 4.1 Iniciando a aplicação local:

Requisitos: Node

Executar o comando NPM abaixo para instalar o Dataform

```
npm i -g @dataform/cli@^3.0.0-beta
```

- 4.2 Inicializar um projeto

dataform init <mark>***PROJECT_PATH***</mark> <mark>***PROJECT_NAME***</mark> <mark>***DEFAULT_LOCATION***</mark>     

+ PROJECT_PATH: caminho onde será iniciado o projeto.
+ PROJECT_NAME: nome do projeto.
+ DEFAULT_LOCATION: região em que você quer o Dataform para gravar dados do BigQuery.

Exemplo:

```
dataform init . myDataformProject southamerica-east1
```

Esse exemplo inicia um projeto na pasta em que ele está, por isso o path `.`. O nome do projeto é `myDataformProject` e a região é `southamerica-east1`, que se refere a SP.

Após isso é para seu projeto estar com a seguinte estrutura
```
   project-dir
   ├── definitions
   ├── includes
   └── workflow_settings.yaml
```

- 4.3 Conectar as credenciais

Executar o comando abaixo:

```
dataform init-creds
```
**SAIDA:**
### ⚠️ Escolher a mesma região do seu dataset no BigQuery ⚠️
```re

[1] US (default)
[2] EU
[3] other

Enter the location of your datasets [1, 2, 3]: 
```
Na segunda saída selecionar a opção JSON Key.

```
[1] ADC (default)
[2] JSON Key

Do you wish to use Application Default Credentials or JSON Key [1/2]: 
```

Nessa opção, você deve inserir o caminho para o arquivo de credenciais da sua conta de serviço, que foi baixado na sua máquina ao cria-lá na ***secção 2***.

Feito essa ação você receberá um retorno de sucesso que suas credenciais foram cadastradas.

> [!CAUTION]
> Se você usa um sistema de controle de origem, não confirme o df-credentials.json. no repositório para proteger essas credenciais. Recomendamos que você adicione o parâmetro .df-credentials.json em .gitignore.

## 5. Criando sua primeira query

- 5.1 O seu local de trabalho será dentro da pasta definitions, então todas as suas views e tabelas devem ser alocadas lá.

Dentro da para ***definitions*** crie um arquivo com o nome de sua preferência com a terminação de .sqlx

Exemplo:
example.sqlx

- 5.2 Sintexe básica sqlx

config { type: '**TABLE_TYPE**' } **SELECT_STATEMENT**

- TABLE_TYPE: o tipo da tabela: **table**, **incremental** ou **view**.
- SELECT_STATEMENT: uma instrução SELECT que define a tabela.

### Exemplo de query para criar uma tabela:
```sql
config {
  type: "table"
}

SELECT * 
FROM `dataform.teste`
```

Nessa caso a query irá criar uma tabela **(type: table)** de nome "example" **(nome do arquivo)**, buscando os dados da tabela teste **(`dataform.teste` é caminho da tabela)**.

- 5.3 Compilação

Para conferir a saída do processo de compilação no terminal, execute o seguinte comando:

```bash
dataform compile
```

Para visualizar a saída do processo de compilação como um objeto JSON, execute o seguinte comando:

```bash
dataform compile --json
```

Para visualizar a saída da compilação com variáveis de compilação personalizadas, execute o seguinte comando:

```bash
dataform compile --vars=SAMPLE_VAR=SAMPLE_VALUE,foo=bar
```

Substitua:
- `SAMPLE_VAR`: sua variável de compilação personalizada.
- `SAMPLE_VALUE`: o valor da variável de compilação personalizada.

---

- 5.4 Execução de Código

Para executar o código do seu projeto no Dataform, execute o seguinte comando:

```bash
dataform run
```

Para executar o código do seu projeto do Dataform no BigQuery com variáveis de compilação personalizadas, execute o seguinte comando:

```bash
dataform run --vars=SAMPLE_VAR=SAMPLE_VALUE,sampleVar2=sampleValue2
```

Substitua:
- `SAMPLE_VAR`: sua variável de compilação personalizada.
- `SAMPLE_VALUE`: o valor da variável de compilação personalizada.

Para executar o código do seu projeto do Dataform no BigQuery e recriar todas as tabelas do zero, execute o seguinte comando:

```bash
dataform run --full-refresh
```

> Sem `--full-refresh`, o Dataform atualiza tabelas incrementais sem reconstruí-las do zero.

---

### Execução em Modo de Simulação

Para conferir o código SQL compilado final adaptado ao estado atual sem executá-lo no BigQuery, execute o seguinte comando:

```bash
dataform run --dry-run
```


## 6. Finalização

Com esses comandos, você agora tem a flexibilidade de manipular diversos datasets, views e tabelas no BigQuery diretamente via Dataform CLI, automatizando e otimizando o gerenciamento de seus dados de forma eficiente.

Para mais informações consulte a documentação oficial do google cloud:
[Documentação](https://cloud.google.com/dataform/docs/use-dataform-cli?hl=pt-br)