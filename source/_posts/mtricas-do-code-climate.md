title: Métricas do Code Climate
date: 2013-03-04 01:36
tags: [metricas, ferramentas]
---


Code Climate é uma ferramenta de análise de código ruby que ajuda a melhorar a qualidade do nosso código. Ele identifica métodos longos e complexos, classes com alto nível de complexidade e blocos duplicados e chama isso de 'Smells'. 

Cada projeto no Code Climate recebe uma pontuação média ponderada (GPA) que vai de 0 a 4.0 e aplica uma pontuação e classificação a sua classe que vai de A a F. 


![CodeClimateScreenShot][codeclimate]



O Code Climate utiliza a gema de métricas [Flog][3], uma variante da métrica ABC. A métrica ABC (Atribuições, Branchs e Condições) calcula o número de atribuições, ramificações sem escopo e condições de um trecho de código, ou seja, apenas diz - 'Escreva métodos menores, essa condicional pode ser melhorada? Tente ser mais preciso, e menos verboso no seu código'. 

Além de medir complexidade, o Code Climate procura por duplicações e trechos de códigos semelhantes, se baseando no [Flay][4]. E medidas de churn e gráficos. Just [DRY][5]! 

Todos esses trechos de códigos complexos indicam que talvez seu código precise ser refatorado. Mas, claro, aqui vale o julgamento do desenvolvedor. Eu tenho uma disputa bem bacana com o Code Climate para melhorar meu código a cada commit. Somos desenvolvedores tentando fazer um bom código, certo? Podemos nos valer dessas ferramentas na tentativa de fazê-lo bem. Além de tudo, Code Climate é bonitão e ajuda na integração contínua. Uma ferramenta para ser ouvida.

O Code Climate apenas aceita projetos do Github e é free para open source. Plug and Play.

[1]: http://codeclimate.com
[2]: http://c2.com/cgi/wiki?AbcMetric
[3]: http://ruby.sadi.st/Flog.html
[4]: http://ruby.sadi.st/Flay.html
[5]: http://en.wikipedia.org/wiki/Don't_repeat_yourself
[codeclimate]: http://69.164.216.134/files/screenshot.png