# GivenWhenThen

Given-When-Then é um estilo de representação de testes

A ideia essencial é dividir a escrita de um cenário (ou teste) em três seções:

- A parte **given** descreve o estado do mundo antes de você iniciar o comportamento que está especificando neste cenário. Você pode pensar nisso como as pré-condições para o teste.
- A seção **when** é aquele comportamento que você está especificando.
- Finalmente, a seção **then** descreve as mudanças que você espera devido ao comportamento especificado.

Exemplo:

- Funcionalidade: O usuário negocia ações
  - Cenário: O usuário solicita uma venda antes do fechamento da negociação
    - **Given/Dado**
      - que tenho 100 ações da MSFT
      - E tenho 150 ações da APPL
      - E o horário é antes do fechamento da negociação
    - **When/Quando**
      - peço para vender 20 ações da MSFT
    - **Then/Então**
      - Eu deveria ter 80 ações da MSFT
      - E deveria ter 150 ações da APPL
      - E uma ordem de venda de 20 ações da MSFT deveria ter sido executada
