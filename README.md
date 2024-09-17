# Manager Archives Python

Guia para gerenciamento de arquivos em Python de forma nativa.

## Descrição

Este repositório fornece exemplos e explicações sobre como realizar operações de leitura e escrita de arquivos utilizando funções nativas do Python.

## Funções de Leitura

### `read()`
Lê todo o conteúdo do arquivo como uma única string.

```python
with open('arquivo.txt', 'r') as arquivo:
    conteudo = arquivo.read()
    print(conteudo)  # Imprime todo o conteúdo do arquivo
```

### `readline()`
Lê uma linha do arquivo de cada vez.

```python
with open('arquivo.txt', 'r') as arquivo:
    linha = arquivo.readline()
    print(linha)  # Imprime a primeira linha do arquivo
```

### `readlines()`
Lê todas as linhas do arquivo e retorna uma lista de strings.

```python
with open('arquivo.txt', 'r') as arquivo:
    linhas = arquivo.readlines()
    print(linhas)  # Imprime uma lista contendo todas as linhas do arquivo
```

## Funções de Escrita

### `write()`
Escreve uma string no arquivo.

```python
with open('arquivo.txt', 'w') as arquivo:
    arquivo.write("Escrevendo uma linha no arquivo.\n")
```

### `writelines()`
Escreve uma lista de strings no arquivo.

```python
with open('arquivo.txt', 'w') as arquivo:
    linhas = ["Linha 1\n", "Linha 2\n", "Linha 3\n"]
    arquivo.writelines(linhas)
```

## Função `lido_e_removido()`

Essa função percorre as linhas de um arquivo, encontra um nome específico, salva essa linha em outro arquivo e remove a linha original.

### Código:
```python
def lido_e_removido(nome_arquivo, nome_procurado, arquivo_saida):
    # Ler todas as linhas do arquivo original
    with open(nome_arquivo, 'r') as arquivo:
        linhas = arquivo.readlines()

    # Abrir o arquivo de saída para escrita
    with open(arquivo_saida, 'w') as saida:
        # Abrir o arquivo original para reescrever
        with open(nome_arquivo, 'w') as arquivo:
            # Percorrer cada linha do arquivo original
            for linha in linhas:
                # Se o nome procurado estiver na linha
                if nome_procurado in linha:
                    # Escrever a linha no arquivo de saída
                    saida.write(linha)
                else:
                    # Reescrever a linha no arquivo original (removendo a que contém o nome)
                    arquivo.write(linha)

# Exemplo de uso
lido_e_removido('dados.txt', 'João', 'encontrados.txt')
```

### Explicação da Função

- **Leitura das Linhas:** Lê todas as linhas do arquivo original `nome_arquivo` e as armazena em uma lista.
- **Escrita no Arquivo de Saída:** Abre o arquivo de saída `arquivo_saida` para escrever as linhas que contêm o `nome_procurado`.
- **Reescrita do Arquivo Original:** Abre o arquivo original para reescrever apenas as linhas que não contêm o `nome_procurado`.
- **Processamento das Linhas:** Percorre cada linha, verifica se o `nome_procurado` está presente, e decide se a linha deve ser movida para o arquivo de saída ou reescrita no arquivo original.

Esse processo assegura que as linhas contendo o nome procurado são movidas para outro arquivo e removidas do arquivo original.
