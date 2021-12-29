# Nomenclatura de testes

Neste artigo vou apresentar algumas estratégias para definir a nomenclatura de testes de unidade que podem usadas para nomear seus testes de unidade.

O nome de um teste de unidade deve ser composto por três partes:

- O nome do método que está sendo testado;
- O cenário em que ele está sendo testado;
- O comportamento esperado quando o cenário é invocado;

Essa definição define um padrão de nomenclatura que é importante, visto que têm a intenção de expressar explicitamente a intenção do teste e isso facilita o entendimento do que esta sendo testado pois:

- Evidencia a operação que estamos testando;
- Indica em que circunstâncias;
- E informa qual é o resultado esperado;

Testes são mais do que apenas verificar se seu código funciona; eles também fornecem documentação. Examinando o conjunto de testes de unidade, você deve poder inferir o comportamento do seu código sem mesmo examinar o código em si.

Além disso, quando os testes falharem, será possível ver exatamente quais cenários não atendem às suas expectativas.

Esse é o objetivo para ter uma convenção de nomes aplicada aos testes de unidade : ser simples, clara e de fácil entendimento.

---

<br>

De acordo com **Roy Osherove**, autor de **The Art of Unit Testing**, uma nomenclatura básica para testes de unidades usa 3 elementos ao definir o nome do teste:

```
[UnitOfWork_StateUnderTest_ExpectedBehavior]
```

Onde:

Uma **UnitOfWork** (_unidade de trabalho_) é um caso de uso no sistema que começa com um método público e termina com um dos três tipos de resultados:

1. Um valor de retorno/exceção;
2. Uma mudança de estado do sistema que muda seu comportamento;
3. Uma chamada para um terceiros (quando usamos mocks);

Portanto, uma _unidade de trabalho_ pode ser pequena como um método, ou tão grande quanto uma classe, ou mesmo várias classes. desde que tudo corra na memória e esteja totalmente sob nosso controle.

Exemplos :

```
public void Sum_NegativeNumberAs1stParam_ExceptionThrown()
public void Sum_NegativeNumberAs2ndParam_ExceptionThrown()
public void Sum_SimpleValues_Calculated()
```

## Variações da nomenclatura de testes de proposta por Roy Osherove.

**1 - MethodName_StateUnderTest_ExpectedBehavior**

_NomeDoMetodo_EstadoEmTeste_Comportamento esperado_

Existem alguns argumentos contra esta estratégia de que se os nomes dos métodos mudam como parte da refatoração do código, então o nome do teste como este também deve mudar ou se torna difícil de compreender em um estágio posterior.

Exemplos:

```
isAdult_AgeLessThan18_False
retirMoney_InvalidAccount_ExceptionThrown
admitStudent_MissingMandatoryFields_FailToAdmit
```

<br>

**2 - MethodName_ExpectedBehavior_StateUnderTest**

_NomDoMetodo_EstadoEsperado_EstadoEmTeste_

Alguns desenvolvedores também recomendam o uso dessa técnica de nomenclatura.

Essa técnica tem a desvantagem de que, se os nomes dos métodos forem alterados, será difícil de compreender em um estágio posterior.

A seguir temos o nome dos testes usando no primeiro item definidos usando esta técnica:

```
isAdult_False_AgeLessThan18
retirMoney_ThrowsException_IfAccountIsInvalid
admitStudent_FailToAdmit_IfMandatoryFieldsAreMissing
```

<br>

**3 - test[Nome do Recurso sendo testado]**

Esta nomenclatura torna mais fácil ler o teste, pois o recurso a ser testado é escrito como parte do nome do teste. Embora haja argumentos de que o prefixo “test” seja redundante.

Abaixo temos os nomes dos testes usando esta estratégia de nomenclatura:

```
testIsNotAnAdultIfAgeLessThan18
testFailToWithdrawMoneyIfAccountIsInvalid
testStudentIsNotAdmittedIfMandatoryFieldsAreMissing
```

<br>

**4 - Nome do Recurso a ser testado**

Muitos desenvolvedores sugerem que é melhor simplesmente escrever o recurso a ser testado, porque, de qualquer forma, se usa anotações para identificar o método como método de teste.

Outra recomendação a esta estratégia é pelo motivo de fazer testes de unidade como forma alternativa de documentação e evitar 'odores' de código.

A seguir temos os nomes dos testes no primeiro exemplo nesta abordagem:

```
IsNotAnAdultIfAgeLessThan18
FailToWithdrawMoneyIfAccountIsInvalid
StudentIsNotAdmittedIfMandatoryFieldsAreMissing
```

<br>

**5 - Should_ExpectedBehavior_When_StateUnderTest**

Esta técnica também é usada por muitos, pois torna mais fácil a leitura dos testes.

A seguir os nomes dos testes nesta abordagem:

```
Should_ThrowException_When_AgeLessThan18
Should_FailToWithdrawMoney_ForInvalidAccount
Should_FailToAdmit_IfMandatoryFieldsAreMissing
```

<br>

**6 - When_StateUnderTest_Expect_ExpectedBehavior**

Veja a seguir como os testes do primeiro exemplo seriam parecidos se fossem nomeados usando esta técnica:

```
When_AgeLessThan18_Expect_isAdultAsFalse
When_InvalidAccount_Expect_WithdrawMoneyToFail
When_MandatoryFieldsAreMissing_Expect_StudentAdmissionToFail
```

<br>

**7 - Given_Preconditions_When_StateUnderTest_Then_ExpectedBehavior**

_Condicoes_EstadoEmTeste_ComportamentoEsperado_

Esta abordagem é baseada na convenção de nomenclatura desenvolvida como parte do **Behavior-Driven Development (BDD)**.

A ideia é dividir os testes em três partes, de forma que se possa chegar a pré-condições, estado em teste e comportamento esperado a ser escrito no formato acima.

A seguir temos o nome do primeiro exemplo se fossem nomeados usando esta técnica:

```
Given_UserIsAuthenticated_When_InvalidAccountNumberIsUsedToWithdrawMoney_Then_TransactionsWillFail
```

O nome resultante fica um pouco longo e talvez não seja o mais indicado.

<br>

## Conclusão

Na verdade existem dezenas de convenções e, na verdade, não importa qual delas você vai escolher, o que importa é que ela seja coerente, simples, clara e que ajude no entendimento do propósito dos testes de unidades. Além disso é importante que ela também seja adotada de maneira uniforme por toda a equipe.

Assim, de forma geral podemos definir as seguintes recomendações para definir a nomenclatura de testes:

- O nome do teste deve expressar um requisito específico;
- O nome do teste pode incluir a entrada ou estado esperado e o resultado esperado para essa entrada ou estado;
- O nome do teste deve ser apresentado como uma declaração ou fato da vida que expressa fluxos de trabalho e resultados;
- O nome do teste pode incluir o nome do método ou a classe testada;

E estamos conversados...

## Referências

- http://www.macoratti.net/20/12/net_unitconv1.htm
