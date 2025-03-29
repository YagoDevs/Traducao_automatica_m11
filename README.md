# Tradução Automática - Implementação da Seção 9.5 do Dive Into Deep Learning

## Aluno: Yago Phellipe Matos Lopes
### Curso: Ciência da Computação

Este repositório contém a implementação do estudo de caso de tradução automática conforme descrito na seção 9.5 do livro "Dive into Deep Learning". A implementação inclui o download e pré-processamento do conjunto de dados do Projeto Tatoeba, tokenização, obtenção do vocabulário e treinamento de um modelo de tradução usando PyTorch.

## Conteúdo

- `traducao_automatica.ipynb`: Notebook com a implementação completa
- `README.md`: Este arquivo com as respostas às perguntas da seção 9.5.7

## Respostas às Perguntas da Seção 9.5.7

### 1. Tente valores diferentes do argumento num_examples na função load_data_nmt. Como isso afeta os tamanhos do vocabulário do idioma de origem e do idioma de destino?

Com base nos resultados obtidos ao executar o código com diferentes valores de `num_examples`, observamos o seguinte:

| Número de Exemplos | Vocabulário de Origem (EN) | Vocabulário de Destino (FR) |
|--------------------|----------------------------|----------------------------|
| 1.000              | 266                        | 321                        |
| 5.000              | 875                        | 1.230                      |
| 10.000             | 1.505                      | 2.250                      |


Quanto mais exemplos a gente usa, maior fica o vocabulário, mas não de forma constante. No começo, ele cresce rápido, depois fica mais devagar. O vocabulário do francês é sempre maior que o do inglês, não importa quantos exemplos a gente use. Isso acontece por causa de diferenças entre as duas línguas, como a conjugação dos verbos e a formação das palavras.

-----

### 2. O texto em alguns idiomas, como chinês e japonês, não tem indicadores de limite de palavras (por exemplo, espaço). A tokenização em nível de palavra ainda é uma boa ideia para esses casos? Por que ou por que não?

Em relação à tokenização em nível de palavra para idiomas como o chinês e o japonês, esta abordagem não se mostra ideal. A ausência de delimitadores explícitos, como espaços, introduz uma ambiguidade significativa na identificação dos limites vocabulares. Uma mesma sequência de caracteres pode ser interpretada de maneiras distintas, dificultando a segmentação precisa. Adicionalmente, as unidades linguísticas fundamentais nestes idiomas operam de forma diferente das línguas que utilizam espaços, tornando a tokenização em nível de palavra menos pertinente. Tentar aplicar essa técnica resultaria em um vocabulário excessivamente extenso e esparso, o que seria computacionalmente desafiador. Por fim, seria necessário um pré-processamento complexo, com segmentadores específicos para cada idioma, para tentar identificar as palavras, o que adiciona complexidade ao processo.
