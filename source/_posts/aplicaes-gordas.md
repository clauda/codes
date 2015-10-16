title: Aplicações Gordas
date: 2013-03-06 12:28
tags: [rails]
---


O desenvolvedor geralmente é um cara preguiçoso, mas isso nem sempre é algo ruim. Costumamos automatizar soluções para os nosso próprios problemas criando ferramentas verdadeiramente fantásticas.

Pelo mesmo motivo (preguiça), e claro, sabiamente tentando não reinventar a roda, nos valemos de 'plugins' que oferecem recursos poderosos prontos. Genial. O problema: frequentemente acontece que precisamos de uma funcionalidade específica e para isso utilizamos alguma ferramenta que vai muito além do que, de fato, precisamos, cheios de bruxarias e malabarismos.

Meu foco a partir daqui são aplicações Rails.


## gem 'bigmac' ##

O Rails sozinho oferece vários recursos que nem sempre precisamos ou que sequer sabemos que existem. Aliado a isso, nosso Gemfile está cheia daquelas gems com +100 features, mas que na real, você só precisa e usa uma ou duas. Estes recursos não utilizados dentro da aplicação, não passam de lixo ou gordura. 

Muitas vezes abusar das gems adiciona uma camada de complexidade que não queremos. No final do seu projeto você vai se sentir como se estivesse em um jogo de [Jenga](http://pt.wikipedia.org/wiki/Jenga). 

Além de trazer uma camada de complexidade, ainda causa uma dependência indesejável. Pense assim: um projeto fica orfão cada vez que uma gem fica depreciada. Cada vez que um projeto fica orfão, morre um koala na Austrália.

Desenvolvedores, além de preguiçosos, conseguem ser extremamente vaidosos com seu código. Exitem gems com finalidade meramente estética. Esse senso de estética do programador também pode comprometer a performace da aplicação. Bonitinho, mas gagueja na resposta.


## A Dieta ##

Não sabemos mais escrever métodos?

Parece exagerado, mas é para gerar reflexão. O que estamos tentando ganhar em tempo, podemos está perdendo em desempenho. Considere se você consegue algum ganho de performance escrevendo suas próprias bibliotecas, em alguns casos. Adicionar uma linha ao Gemfile para resolver um problema de simples resolução, ainda que rico em calorias, é tentador. Sem dúvida, rápido, objetivo ou não.

Aqui vale ponderar sobre a necessidade de plugar uma gem a mais na sua aplicação.  Quando é meramente estética, ou quando decidimos com a pressão do prazo estourando, ou estamos com pura e violenta preguiça? Acrescente o fato de que você pode estar perdendo uma puta oportunidade de conhecer e praticar mais sobre vários conceitos bacanas. O quão é relevante manter um regime on rails? 


