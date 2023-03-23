## Descrição
Com a ampliação do ecossitema Solfácil, um produto foi idealizado para facilitar o monitoramento das usinas financiadas através da Solfácil.

O parceiro Solfácil pode cadastrar usinas que ele fez a instalação e financiamento através da Solfácil nesta plataforma.

Por enquanto precisamos criar dois fluxos na API que futuramente serão consumidas pelo frontend, sendo eles:

- Criação do cadastro de um parceiro;
- Criação das usinas dentro da plataforma;

Dados esses dois fluxos, seguem abaixo as especificações para cada um deles:

## Especificações

### Banco de dados

#### Partner

A empresa parceira deve conter os seguintes dados:

##### Atributos

```
- id: [uuid]
- name: [string]
- cnpj: [string] - (fazer a validação mínima de quantidade de caracteres)
- email: [string] - (verificar se o email é válido)
- password: [string]
- created_at: [datetime]
- updated_at: [datetime]
```

**TODOS OS CAMPOS SÃO OBRIGATÓRIOS**

#### Plant

A usina deve conter os seguintes dados:

##### Atributos

```
- id: [uuid] 
- nome: [string]
- cep: [string] - (fazer a validação mínima de quantidade de caracteres)
- latitude: [float]
- longitude: [float]
- capacidade_maxima_GW: [int]
- created_at: [datetime]
- updated_at: [datetime]
```

**TODOS OS CAMPOS SÃO OBRIGATÓRIOS**

## Desafio
- Crie uma API RESTful para criar, ler, atualizar e excluir parceiros
- Nesta mesma API e implemente um endpoint de consulta SQL para recuperar os 10 últimos parceiros cadastrados.
Exemplo:
```
[GET] http://solarium.solfacil.com/last-partners
```

- Crie uma API RESTful para criar, ler, atualizar e excluir usinas
- Nesta mesma API e implemente um endpoint de consulta SQL para recuperar as 5 usinas de maior capacidade. 
Exemplo:
```
[GET] http://solarium.solfacil.com/top-capacity-plants
```

### Endpoints

Para ambas as entidades, precisamos criar endpoints de **criação**, **listagem** e **busca através do id**, eles devem seguir o seguinte formato:

#### Listagem

Os endpoints de listagem devem utilizar o verbo http **GET**.
Nestes endpoints não será necessário nenhum tipo de parâmetro, eles devem retornar **TODOS** os registros salvos no banco de dados.

Exemplo:
```
[GET] http://solarium.solfacil.com/partners
```

#### Busca por id

Os endpoints de busca por **ID** também devem utilizar o verbo http **GET**.
Nestes endpoints será necessário enviar um parâmetro através da rota, que é o Identificador da entidade buscada, este endpoint deve
retornar apenas um registro (o com o id enviado).

Exemplo:
```
[GET] http://solarium.solfacil.com/partners/42
```

#### Criação

Os endpoints de criação devem utilizar o verbo http **POST**.
Nestes endpoints todos os atributos para a criação da entidade serão enviados através do **body**, devendo ser enviados em formato de **JSON**.

Exemplo:
```
[POST] http://solarium.solfacil.com/partners

[BODY] - application/json
{
  ...
  "name": "Teste Solarium",
  ...
}
```


### Adicionais

- Validações adicionais para a criação dos registros, como cnpj, email e afins;
- Documentação das funções públicas;
- Testes unitários;
