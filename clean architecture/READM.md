## Clean Architecture

 Na aplicação da arquitetura limpa, nós organizamos nossas unidades de código em componentes e precisamos sempre pensar nas unidades como partes de uma solução. Os diferentes componentes são organizados em camadas, e cada camada tem sua responsabilidade.

Pensando em componentes, podemos também isolar as responsabilidades de cada unidade de código, e pensar em unidades menores e especializadas. Isso é uma das regras da codificação de unidades de código, quando trabalhamos com a construção dos componentes. Precisamos de unidades especializadas e com responsabilidades únicas e bem definidas. Não podemos criar uma estrutura com classes generalistas, ou com muito código complexo num mesmo lugar, sob pena de impactar a qualidade do código.

O uso de camadas de software não é uma ideia nova, mas ainda assim é pouco aplicada quando pensamos em código, porque não conseguimos enxergar, de forma visual, o que cada camada faz. Por isso, um outro modo de pensar em camadas são grupos de componentes com responsabilidades semelhantes. No caso de uma camada de Casos de Uso, por exemplo, não podemos ter nenhum código que execute tarefas de conexão com Bancos de Dados, como criar a conexão. Pensando dessa forma, olhamos nosso projeto não como camadas de um bolo, e sim como camadas de uma cebola. É dessa forma que a Arquitetura Limpa pensa a criação das camadas e do código de cada camada.

Usamos, para guiar a qualidade do código, os conceitos de SOLID, definidos nos livros Clean Code e Clean Architecture, de Robert C. Martin. Estes conceitos se tornaram um guia de implementação de código de qualidade e são amplamente discutidos em livros, vídeos e artigos, com aplicação em diferentes linguagens de programação. 

## SOLID é um acrônimo, em língua inglesa, para cinco princípios: 

Single Responsability Principle, ou Princípio da Responsabilidade Única, define que uma unidade de código só deve ter uma responsabilidade e deve ter um único motivo para mudar. Assim, uma unidade de código deve ser especializada no que faz e no uso que é feito dela. Não pode ser responsável, por exemplo, por alterar sua resposta dependendo do tipo de chamada.
Vamos imaginar uma pessoa atendente de uma lanchonete. Ela tem, no processo de venda de lanches, um propósito específico, que é anotar o pedido, entregar para a cozinha, registrar o pagamento e posteriormente entregar o lanche. A responsabilidade dessa pessoa é clara: servir como uma interface entre o(a) cliente e a cozinha, e faz isso de forma padronizada para todas as requisições que chegam, ou seja, de acordo com os(as) clientes que chegam a cada momento. O código deve ser assim, com uma responsabilidade clara, e que faça apenas o que precisa ser feito.
