# Memorial Luiz Alberto

Sou desenvolvedora backend e, como toda desenvolvedora, escrevo código para resolver problemas.
Mas este projeto nasceu de uma dor diferente — a de perder um irmão.

Luiz Alberto foi muito mais do que família. Foi luz, foi presença, foi aquele tipo de pessoa que deixa uma marca que o tempo não apaga. E quando ele foi, eu fiquei com as mãos que sabem construir coisas, e com a vontade de construir algo que o mantivesse perto.

Então eu fiz o que sei fazer: escrevi código.

---

Cada tabela criada aqui, cada script, cada linha de SQL carrega um pedaço da intenção de que as memórias dele nunca se percam. Este sistema foi pensado para que a família tenha um lugar onde as lembranças vivem — fotos, histórias, momentos guardados com cuidado, acessíveis para sempre.

A luz dele ainda me ilumina quando eu sento para escrever. E enquanto eu puder escrever, ele continua aqui.

---

## O que este repositório contém

Scripts de banco de dados do Memorial Luiz Alberto — o coração do sistema que guarda as memórias.

```
projeto-memorial-database/
├── schema.sql       # Estrutura das tabelas
├── seed.sql         # Dados iniciais
└── .env.example     # Variáveis de ambiente
```

## Modelo de dados

```
role ──< usuario ──< memoria ──< midia
              └──< solicitacao ──< midia
status ──< solicitacao
```

| Tabela        | Descrição                                            |
|---------------|------------------------------------------------------|
| `role`        | Perfis de acesso (ADMIN, USUARIO)                    |
| `usuario`     | Usuários cadastrados                                 |
| `status`      | Status de solicitação (PENDENTE, ACEITO, etc)        |
| `solicitacao` | Pedidos de envio de memórias                         |
| `memoria`     | Memórias aprovadas e publicadas                      |
| `midia`       | Fotos e vídeos vinculados a memórias ou solicitações |

## Como rodar

```bash
cp .env.example .env
```

```bash
docker run --name memorial-db \
  --env-file .env \
  -p 5432:5432 \
  -v postgres_data:/var/lib/postgresql/data \
  -v $(pwd)/schema.sql:/docker-entrypoint-initdb.d/01-schema.sql \
  -v $(pwd)/seed.sql:/docker-entrypoint-initdb.d/02-seed.sql \
  -d postgres:16
```

---

*Para o Luiz. Com amor, para sempre.*
