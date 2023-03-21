## Colocar um elemento em uma lista
> L de left
```
LPUSH ultimas_noticias "Jogador de basqueste..."
```

## Para manter elementos do parametro que é passado, e descartar o resto
> Lembrando que trim = aparar, essa é a logica
```
LTRIM ultimas_noticias 0 2
```

## Para visualizarmos o textos em sua posição na lista
```
LINDEX ultimas_noticias 0
```

## Tamanho da lista
```
LLEN ultimas_noticias
```

## Filtrar mais de um elemento por meio de posições
```
LRANGE ultimas_noticias 1 2 
```

# Para remover e recuperar o primeiro elemento de uma fila
```
LPOP "fila:confirma-email"
```

# Para remover e recuperar o último elemento de uma lista
```
RPOP "fila:confirma-email"
```

### BLPOP
> Como evitar Busy Waiting , que é fazer a maquina trabalhar mesmo enquanto espera a chegada de uma determinada coisa.
```
BLPOP fila:confirma-email 30
```

Sendo assim ele espera 30 segundos para avisar que chegou por exemplo um email. E se chega ele desbloqueia os segundos e executa.

> Sem definir o time-out - Importante para ele esperar para sempre e quando chegar algo, aí sim ele executa.

```
BLPOP fila:confirma-email 0
```

## Fazer conjuntos

```
SADD "relacionamento:leonardo" "vitoria"
```

> Conjuntos não aceita dados que se repetem

## Para ver quantos elementos tem em um conjunto - "cardinalidade"

```
SCARD "relacionamento:leonardo" 
```

## Para ver quais elementos tem dentro do conjunto  
```
SMEMBERS "relacionamento:leonardo" 
```

## Para ver se tem algum elemento especifico no conjunto 

```
SISMEMBERS "relacionamento:leonardo" "vitoria"
```

## Remover algum elemento no conjunto

```
SREM "relacionamento:leonardo" "vitoria"
```

## Fazer um intersecção entre dois conjuntos (saber a igualdade)
```
SINTER "relacionamento:leonardo" "relacionamento:yasmin"
```

## Saber a diferença do 1° conjunto pro 2° conjunto
```
SINTER "relacionamento:leonardo" "relacionamento:yasmin"
```

## Fazer união de elementos de dois ou mais conjuntos

```
SUNION "relacionamento:leonardo" "relacionamento:yasmin"
```

# Diferença da lista e conjunto

> Quando utilizamos conjuntos, não conseguimos recuperar um elemento em um determinado índice, pois não temos garantia de que a ordem dos valores será mantida. Outra diferença em relação as listas, é que conjuntos não permitem elementos repetidos.
