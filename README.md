![image](https://github.com/user-attachments/assets/22e37c83-8937-4db2-8adf-00bc39809f20)![image](https://github.com/user-attachments/assets/c8562676-61ef-425d-99e6-a1fe9ca8f5b6)# Passo a passo
[DOCUMENTAÇÃO SEGUIDA](https://cloud.google.com/dataform/docs/workspace-compilation-overrides?hl=pt-br&_gl=1*7eejrx*_ga*MTc0NzUwODUyLjE3MjI0NTMwNzA.*_ga_WH2QY8WWF5*MTcyNTU2NTM1Ny4xOS4xLjE3MjU1NjU5OTIuMy4wLjA.)

### Passo 1 - Criar repositórios
Criar um repositório no Bitbucket:

![image](https://github.com/user-attachments/assets/56fd27b2-e7c0-4bd3-8539-e49bba3b0404)

Criar um repositório no Dataform:

![image](https://github.com/user-attachments/assets/8728eff7-3622-489a-ad09-27d4de9e81ce)

### Passo 2 - Criar chaves SSH

Abir gitbash ou powershell (Windows) e realizar comando para criação das chaves SSH:

`ssh-keygen -t rsa -b 2048 -C "your_email@example.com"`

![image](https://github.com/user-attachments/assets/dbe34243-f9c5-4c9a-b029-09cdf40badbc)

### Passo 3 - Inserir chaves SSH nos repositórios

Inserir public SSH key no repositório do bitbucket
![image](https://github.com/user-attachments/assets/f74f66b9-3296-40ee-b6aa-340c378dde7e)

Criar uma secret no google cloud plataform:

![image](https://github.com/user-attachments/assets/6c3a84d5-9f2b-4ea5-abcd-66d85c4c4ff9)

Inserir KeyPrivada no key value do secret GCP:

![image](https://github.com/user-attachments/assets/23f61e61-cc42-4034-86e8-4f5901c9f319)

### Passo 4 - Gerenciar permissões

Atribuir cargo de secretAcessor ao seu serviço:

`service-PROJECT_NUMBER@gcp-sa-dataform.iam.gserviceaccount.com`

![image](https://github.com/user-attachments/assets/1e4622b3-c0c3-4efb-8a26-d36029b31b23)

### Passo 5 - Criar conexão entre repositórios

No Dataform, dentro do seu repositório clicar em conectar com GIT

![image](https://github.com/user-attachments/assets/eeae579d-8528-4559-a1ec-e0ee632cbe73)

Preencher com as devidas informações, lembrando que em `valor da chave pública do host SSH` deve-se inserir o valor da sua chave publíca sem o HOST:

![image](https://github.com/user-attachments/assets/65385bfe-25ee-4bfa-a439-e931facc2bf3)

### FEITO TUDO ISSO

Chegamos no erro que não consigui resolver:

![image](https://github.com/user-attachments/assets/7534e45d-f12d-47a1-9111-d49c9819bda8)


