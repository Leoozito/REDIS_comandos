# Instalação

http://redis.io/download

# Comandos
## Startar o server
```
<path_redis>/src
./redis-server
```
## Startar o "comand line interface"
```
<path_redis>/src
./redis-cli
```
## Simples teste na _cli_ para testar conexão
```
ECHO "estou no redis"
```
## Setando o valor para uma chave
```
SET "total_de_cursos" 105
OK
```
## Lendo o valor de uma chave (vem _nil_ quando ela não esta definida)
```
GET "total_de_cursos"
"105"
```
## Atualizando o valor de uma chave que já existia
```
SET "total_de_cursos" 106
OK

GET "total_de_cursos"
"106"
```
## Deletando um chave
```
DEL "total_de_cursos"
GET "total_de_cursos"
(nil)
```
## Consultando as chaves existentes 
```
KEYS * 
```
> \* pesquisa um ou mais caracter, ? um caracter qualquer, [12] 1 ou 2

> *teste  => todas as chaves que terminam com a palavra teste

> b?la    => qualquer caracter, traria bala, bela, bila, b0la ...

> lut[ao] => tras as chaves luta e luto

## Setando Multiplos valores de uma unica vez
```
MSET resultado:03-05-2015:megasena "1, 3, 17, 19, 24, 26" resultado:22-04-2015:megasena "15, 18, 20, 32, 37, 41" resultado:15-04-2015:megasena "10, 15, 18, 22, 35, 43"
OK
```
## Setando valores em hash para uma chave
```
HSET resultado:24-05-2015:megasena "numeros" "13, 17, 19, 25, 28, 32"
(integer) 1
HSET resultado:24-05-2015:megasena "ganhadores" 23
(integer) 1

resultado:24-05-2015:megasena {
 "numeros":   "13, 17, 19, 25, 28, 32",
 "ganhadores": 23
}
```
## Lendo valores de um hash
```
HGET resultado:24-05-2015:megasena "ganhadores"
"23"
```
## Deletando uma chave de um hash
```
HDEL resultado:24-05-2015:megasena "numeros"
(integer) 1
HGET resultado:24-05-2015:megasena "numeros"
(nil)
```
## Criando um hash com multiplos valores de uma única vez
```
HMSET "sessao:usuario:1675" "nome" "guilherme" "total_de_produtos" "3" "sobrenome" "silveira"
OK
```
## Informando um periodo de 'validade' para a chave (em segundos)
```
EXPIRE "sessao:usuario:1675" 1800
(integer) 1
```
## Consultando quanto tempo uma chave ainda vai existir (em segundos)
```
TTL "sessao:usuario:1675"
(integer) 1680

// Após expirar a consulta retorna _nil_
HGET "sessao:usuario:1675" "nome"
(nil)
```
## Incrementar "1" a uma chave
// Se ela não existir é criada com o valor 1
```
INCR pagina:/contato:25-05-2015
(integer) 10
```
## Decrementar "1" ao valor de uma chave
```
DECR pagina:/contato:25-05-2015
(integer) 9
```
## Incrementar uma chave por X (no exemplo 15)
```
INCRBY compras:25-05-2015:valor 15
(integer) 15
```
## Decrementar uma chave por X (no exemplo 2)
```
DECRBY compras:25-05-2015:valor 2
(integer) 13
```
## Incrementar uma chave com valores float (no exemplo 10.50)
```
INCRBYFLOAT compras:25-05-2015:valor 10.50 
"42.5"
```
## Decrementar uma chave com valores float (no exemplo 0.50)
```
DECRBYFLOAT compras:25-05-2015:valor 0.50 
"42.0"
```
## Setando uma chave com _bit_ (ideal para trabalhar com booleanos)
```
SETBIT acesso:25-05-2015 15 1
(integer) 0
```

## Lendo uma chave de _bit_
```
GETBIT acesso:25-05-2015 15
(integer) 1
```

## Saber a quantidade total somada de bits de uma chave
```
BITCOUNT acesso:25-05-2015
```

## Inserindo um operador de AND
```
BITOP AND acesso:25-e-26-05-2015 acesso:25-05-2015 acesso:26-05-2015
```

## Inserindo um operador de OR
```
BITOP OR acesso:25-ou-26-05-2015 acesso:25-05-2015 acesso:26-05-2015
```
> uma chave armazenando bits de duas chaves
# Adicional do aprendizado
Tudo que armazenamos no redis, são valores cacheados, por isso o recomendado é ter um BD armazenando dados, processar os dados e armazenar os dados no REDIS, para que seja rapida a pesquisa.
