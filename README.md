# Challenge

Processamento e leitura de quantidade grande quantidade de dados

## Desafio da Shopback

Tendo como base um banco nosql, temos que processar as informações de todas tabelas e gerar uma nova tabela.
O imporante é que o script consuma a menor quantidade de recursos do servidor, seja de fácil entendimento e manutenção

Linguagem preferencial: PHP 
Banco preferencial: Mongo
Script deve ser escrito para ser executado em shell

## Tabelas:
1) O banco a primeira tabela tem mais 100 milhões de registros e de envios.
2) A tabela de usuário tem mais de 30 milhões de registros.
3) A terceira tabela contém os valores de pedidos de venda.
4) A quarta tabela contém os carrinhos e produtos.
5) A quinta tabela contém o produto e categoria.

## Resultados:

#### A nova tabela deve conter:
* Perfil de gastos mensal.
* Perfil de gastos por categoria mensal.
* Média dos últimos 3 meses de gastos mensal.
* Média dos últimos 3 meses por categoria mensal.
* Informações de usuários.

#### O que se espera de código
* Criação de banco e tudo que for necessário para performance
* Criação de script de extração
* Criação de script de inserção
* Criação de script de leitura da informação.

#### Será avaliado ao executar os scripts:
* Tempo de processamento.
* Tempo de leitura.
* Manter e otimizar estrutura de tabela.


## Estrutura das tabelas 
A estrutura é imutável.

#### Tabela de envio
```
{
    "_id" : ObjectId("59088b68d5871782053dea1d"),
    "campaign_id" : "58827845cd2f5b103d0f5ba6",
    "client_id" : "57587ad57fb83436bb594504",
    "customer_id": "58d549d3808c3c0b89263d51",
    "updated_at" : ISODate("2017-05-26T17:50:13.000Z"),
    "created_at" : ISODate("2017-05-02T13:36:40.000Z"),
    "calls" : 91845
}
```

### Tabela com dados de usuário
```
{
    "_id" : ObjectId("58dec91ecd2f5b663934de21"),
    "customer_id" : "58d549d3808c3c0b89263d51",
    "email" : "joselito@aol.com",
    "details" : {
        "first_name" : "joselito",
        "last_name" : "mesquita",
        "full_name" : null,
        "birthdate" : null,
        "age_group" : null,
        "telephone" : "9999123456",
        "identification" : [ 
            {
                "type" : "cpf",
                "typeName" : "CPF",
                "number" : "0000001010"
            }
        ]
    },
    "address" : [ 
        {
            "address" : null,
            "number" : null,
            "address_complement" : null,
            "city" : "Bacabal",
            "state" : "MA",
            "country" : "Brasil",
            "zipcode" : "65700000",
            "is_primary" : true
        }
    ],
    "updated_at" : ISODate("2017-04-01T00:55:25.000Z"),
    "created_at" : ISODate("2017-03-31T21:24:46.000Z")
}
```

#### Tabela de pedidos
```
{
    "_id" : ObjectId("58812ee70afc660de522c097"),
    "client_id" : "56d484398a20ed6c41598e16",
    "customer_id" : "58812e310afc660dbe1d0982",
    "cart_id" : "58812eaa0afc660dc06a2278",
    "details" : {
        "id" : "704531573027",
        "price" : 379.96
    },
    "info" : {
        "utm_source" : false,
        "utm_medium" : false,
        "utm_campaign" : false,
        "utm_term" : false,
        "utm_content" : false
    },
    "anonymous" : false,
    "updated_at" : ISODate("2017-01-19T21:25:59.000Z"),
    "created_at" : ISODate("2017-01-19T21:25:59.000Z")
}
```
#### Tabela de carrinhos

``` 
{
    "_id" : ObjectId("592872ad808c3c2a1d55204c"),
    "client_id" : "56d48438d2c39468a21494a4",
    "customer_id" : "59286c5b9d1b502aa37210a4",
    "products" : [ 
        {
            "product_id" : "584c477ccd2f5b78d554dfbb",
            "price" : 269.9,
            "quantity" : 1.0
        },
        {
            "product_id" : "584c477ccd2f5b78d554dfb1",
            "price" : 268.9,
            "quantity" : 3.0
        }
    ],
    "amount" : 269.9,
    "info" : {
        "utm_source" : false,
        "utm_medium" : false,
        "utm_campaign" : false,
        "utm_term" : false,
        "utm_content" : false
    },
    "anonymous" : false,
    "complete" : false,
    "recovered" : false,
    "updated_at" : ISODate("2017-05-26T18:24:21.000Z"),
    "created_at" : ISODate("2017-05-26T18:23:41.000Z")
}
```
#### Tabela de produtos
```
{
    "_id" : ObjectId("584c4753cd2f5b713808e334"),
    "client_id" : "56d48438d2c394657c2adb7b",
    "title" : "Ionto Vita Slim",
    "description" : "Eletrocosmético para tratamento de gordura localizada, principalmente masculina e de mulheres acima de 40 anos, e celulite, devido a sua altíssima concentração de ativos (34,5% de ativos) e sinergia com o ativo especializado Pheoslim. Indicado como auxiliar em procedimentos estéticos. Sua formulação contém algas e extratos vegetais, que são ricos em flavonoides, oligoelementos, saponinas, nucleoproteínas, lecitina, mucina. Potencializa os resultados se usado como base em aplicação de faixa gessada, pelo seu efeito oclusivo, ou após a aplicação de máscaras de argila, termoterapia ou crioterapia. Ótimo para ser associado à vinhoterapia e destoxi-redução.",
    "categories" : [ 
        "Cosméticos", 
        "Cosméticos Profissionais", 
        "Líquidos", 
        "Gordura Localizada"
    ],
    "subcategories" : [ 
        "Ionto", 
        "Vita", 
        "Slim", 
        "Buona"
    ],
    "price" : 152.37,
    "normal_price" : 169.3,
    "active" : true,
    "updated_at" : ISODate("2017-05-26T06:40:32.000Z"),
    "created_at" : ISODate("2016-12-10T18:20:02.000Z"),
    "synced" : true
}
```
