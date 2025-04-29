
# Análise de Sentimento com spaCy e Regras Personalizadas

Este script em Python utiliza a biblioteca spaCy para realizar análise de sentimentos em frases em português. Ele emprega regras personalizadas definidas com o `Matcher` para identificar palavras e expressões que indicam sentimentos positivos ou negativos. Uma extensão personalizada é adicionada ao objeto `Doc` do spaCy para armazenar o sentimento detectado em cada frase.

## Funcionamento do Código

1.  **Instalação e Carregamento:**
    * O script primeiro carrega o modelo de linguagem português `pt_core_news_sm` do spaCy. Certifique-se de que o spaCy esteja instalado (`pip install spacy`) e o modelo baixado (`python -m spacy download pt_core_news_sm`).

2.  **Definição de Regras:**
    * Utiliza o `Matcher` do spaCy para criar regras de detecção de palavras e expressões.
    * São definidas listas de palavras e frases consideradas positivas (`positive_patterns`) e negativas (`negative_patterns`).
    * Essas regras são adicionadas ao `Matcher` com os IDs "POSITIVE" e "NEGATIVE", respectivamente.

3.  **Extensão Personalizada `Doc.sentiment`:**
    * Uma extensão personalizada chamada `sentiment` é adicionada ao objeto `Doc` do spaCy usando `Doc.set_extension()`. Essa extensão armazenará o sentimento detectado para cada documento (frase processada). O valor padrão é `None`.

4.  **Função `analyze_sentiment(doc)`:**
    * Esta função recebe um objeto `Doc` do spaCy como entrada.
    * Ela aplica o `Matcher` ao documento para encontrar ocorrências das palavras e expressões definidas nas regras positivas e negativas.
    * A função conta o número de correspondências positivas e negativas.
    * Baseado na contagem, o sentimento do documento é determinado:
        * "Positivo" se houver mais correspondências positivas.
        * "Negativo" se houver mais correspondências negativas.
        * "Neutro/Misto" se houver correspondências positivas e/ou negativas, mas sem uma clara predominância.
        * "Não detectado" se nenhuma palavra ou expressão de sentimento for encontrada.
    * O sentimento detectado é armazenado na extensão `doc._.sentiment`.

5.  **Análise de Frases:**
    * Uma lista de frases em português é definida.
    * O script itera sobre essa lista, processando cada frase com o modelo `nlp` para criar um objeto `Doc`.
    * A função `analyze_sentiment()` é chamada para cada `Doc` para determinar seu sentimento.
    * O script imprime a frase original e o sentimento detectado.

## Integrantes

* **Nome:** Danilo Ramalho Silva      | **RM:**   555183
* **Nome:** Israel Dalcin Alves Diniz | **RM:**   554668
* **Nome:** João Vitor Pires da Silva | **RM:**   556213
* **Nome:** Pablo Menezes Barreto     | **RM:**   556389
* **Nome:** Tiago Toshio Kumagai Gibo | **RM:**   556984
