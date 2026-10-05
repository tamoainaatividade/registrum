# REGISTRUM

## Um sistema de registro epistêmico ponto-a-ponto

> ## **Uma proposta em síntese para os problemas mapeados da AGI —
> ## com raízes epistêmicas de três mil anos.**
>
> **Não encarece o ataque. Barateia a conferência.**

**AMARYAPU** · `CC BY-SA` · receita zero · 2026

---

## Resumo

Uma versão puramente ponto-a-ponto do registro verificável permitiria que uma afirmação fosse
conferida diretamente por qualquer pessoa, sem passar por uma instituição de credibilidade.
As assinaturas digitais e o endereçamento por conteúdo resolvem parte do problema, mas o
benefício principal se perde enquanto for necessário um terceiro de confiança para decidir
**quem pode falar**.

Propomos uma solução para o problema do **duplo-relato** — duas versões incompatíveis do mesmo
evento, sem meio de saber qual foi registrada primeiro — usando uma rede ponto-a-ponto de
documentos endereçados por conteúdo, ancorados em cadeia de carimbos de tempo.

A diferença central em relação aos sistemas de consenso por prova-de-trabalho é de direção:
**não encarecemos o ataque — barateamos a verificação.** Mostramos que, num domínio onde o
custo de examinar excede o custo de classificar, a segurança não vem de tornar a falsificação
cara, mas de tornar a conferência trivial e a contradição estruturalmente inescapável.

Enquanto o custo de conferir for menor que o custo de acreditar, a rede converge para o registro
conferível, e a desqualificação da testemunha deixa de ser a jogada mais barata disponível.

---

## 1 · Introdução

O conhecimento público passou a depender quase exclusivamente de instituições que funcionam como
terceiros de confiança para validar afirmações. O arranjo funciona bem o bastante para a maior
parte dos casos, mas carrega a fraqueza inerente ao modelo baseado em confiança: **a validação
é revogável, e é revogável pela própria instituição que a concedeu.**

O custo dessa revogabilidade não é distribuído. Ele recai inteiramente sobre quem afirma. Uma
afirmação não precisa ser refutada para deixar de circular — basta que quem a fez seja
reclassificado. O procedimento é mais barato que a refutação, produz o mesmo resultado prático,
e não deixa registro de ter sido empregado.

> Chamamos esse procedimento de **§2º**: *não se refuta a afirmação; desqualifica-se quem a fez,
> antes do exame.*

A assimetria de custo é a condição que o mantém operando. Definimos:

```
C8 = custo de examinar ÷ custo de categorizar
```

Enquanto `C8 ≫ 1`, classificar sem examinar é a estratégia dominante para qualquer agente sob
restrição de tempo — independentemente de intenção. **O mecanismo não requer má-fé. Requer
pressa.**

O que é necessário é um sistema de registro baseado em **prova de procedência** em vez de
confiança, permitindo que duas partes quaisquer confiram uma afirmação diretamente, sem a
necessidade de um terceiro que autorize quem pode afirmá-la.

---

## 2 · Afirmações

Definimos uma **afirmação** não como uma sentença, mas como uma tupla:

```
A = ⟨ conteúdo, etiqueta, procedência, data, condição-de-falsificação, campo-de-contradição ⟩
```

Nenhum dos seis campos é opcional. A ausência de qualquer um invalida a afirmação —
não a torna falsa, torna-a **inadmissível como registro**.

### 2.1 · A etiqueta

A etiqueta declara **o tipo de verificação aplicável**, e com ela a regra de falsificação:

| etiqueta | como se derruba |
|---|---|
| `FATO` | apresentando fonte contrária de igual ou maior proximidade ao evento |
| `CÁLCULO` | refazendo a operação e obtendo outro resultado |
| `DECLARADO` | demonstrando que o declarante não poderia ter observado o que declara |
| `TRANSMITIDO` | quebrando a cadeia: mostrando que o elo não existiu |
| `DEMOGRÁFICO` | apresentando a base e a margem |
| `INTERPRETATIVO` | oferecendo leitura alternativa compatível com os mesmos fatos |
| `PROPOSTA` | — **não se derruba.** Marca o que ainda não tem método |
| `FICÇÃO` | — declarada como tal |
| `A CONFERIR` | **fechando a pendência** |

> **A contribuição aqui não é a taxonomia. É a obrigatoriedade.** Uma afirmação sem etiqueta é,
> no sistema, equivalente a uma transação sem assinatura: não é rejeitada por ser falsa, é
> rejeitada por ser **informe**.

### 2.2 · O campo de contradição

Este é o campo que não existe nos sistemas atuais, e é o que o sistema existe para criar.

Toda afirmação carrega um **slot anexável** no qual qualquer parte — e obrigatoriamente **a parte
descrita** — pode acrescentar o que a contradiz. O anexo **viaja com o registro** e é endereçado
pelo mesmo mecanismo.

> **A parte descrita derruba a descrição.** Não por cortesia: por protocolo. Um registro cujo
> campo de contradição seja inacessível à parte descrita é malformado.

---

## 3 · O problema do duplo-relato

O análogo informacional do gasto-duplo não é a mentira. É mais sutil e mais comum:

> **Duas versões incompatíveis do mesmo evento, cada uma internamente coerente, sem meio
> disponível de determinar qual foi registrada primeiro.**

A solução habitual é introduzir uma autoridade central — uma instituição, um veículo, um
selo — que decide qual versão é a válida. O problema dessa solução é o mesmo que Nakamoto
identificou para a casa da moeda: **o destino de todo o sistema passa a depender de quem
opera a autoridade**, e toda afirmação precisa passar por ela.

Como em transações, **a afirmação mais antiga é a que conta**; versões posteriores
incompatíveis são registradas, não apagadas. E a única forma de confirmar a ausência de um
registro anterior é **estar ciente de todos os registros** — o que exige que sejam anunciados
publicamente.

---

## 4 · Endereçamento por conteúdo, e por que não usamos prova-de-trabalho

Um documento endereçado pelo hash do próprio conteúdo tem a propriedade de que **qualquer
alteração produz outro endereço.** A verificação de integridade custa uma operação de hash.

> **Isto já resolve a imutabilidade, e resolve de graça.** Não é necessário despender energia
> para tornar a alteração cara: basta que a alteração seja **detectável**.

### 4.1 · A inversão

A prova-de-trabalho resolve um problema que **não é o nosso**. Ela existe para ordenar eventos
sem autoridade, num ambiente onde o atacante lucra reescrevendo o passado.

Aqui, o atacante típico **não reescreve o registro**. Ele:

1. **não cria o campo** onde a contradição caberia *(M1)*;
2. **deixa o documento público e caro de encontrar** *(M5 moderno)*;
3. **reclassifica a testemunha** *(M4)* — operação que não toca o registro.

> **Nenhuma dessas três é impedida por tornar a escrita cara.** As três são derrotadas por tornar
> **a leitura barata.**

```
segurança_bitcoin  = f( custo de reescrever )     → maximizar
segurança_registrum = f( 1 / custo de conferir )  → minimizar o denominador
```

### 4.2 · Ordenação

Precisamos ainda de ordem temporal, e ela se obtém por **ancoragem periódica**: agrega-se o
conjunto de registros do período numa árvore de Merkle e publica-se **apenas a raiz** em um
meio de difusão ampla e custo marginal desprezível.

A raiz prova que todo o conjunto existia naquele instante. O custo de ancorar é independente do
número de registros ancorados — **uma propriedade que torna o sistema mais barato à medida que
cresce**, invertendo a economia habitual do arquivamento.

---

## 5 · A rede

1. Uma afirmação é composta com os seis campos e endereçada por conteúdo.
2. O endereço é difundido. Quem recebe pode conferir a integridade com uma operação.
3. Periodicamente, as raízes de Merkle do período são ancoradas publicamente.
4. Qualquer nó pode **fixar** (*pin*) qualquer registro. Fixar é o ato que confere permanência.
5. A parte descrita pode anexar contradição a qualquer momento; o anexo é endereçado e difundido
   do mesmo modo e passa a viajar com o original.
6. Pendências `A CONFERIR` permanecem **visíveis** até que alguém as feche, e o fechamento é
   ele próprio um registro.

> **Não há consenso sobre a verdade. Há consenso sobre o que foi dito, por quem, quando, e o que
> foi anexado em contrário.** O julgamento permanece com o leitor — que é o único lugar onde
> ele sempre esteve.

---

## 6 · Permanência, e a honestidade sobre ela

O endereçamento por conteúdo **não garante persistência**. Um registro permanece disponível
enquanto ao menos um nó o mantiver fixado. Sem ninguém fixando, ele desaparece da rede.

> **Descentralizado não significa eterno. Significa que não depende de um só.**

Isto não é defeito: é a devolução da permanência a quem pode decidi-la. As camadas:

| camada | o que entrega | custo |
|---|---|---|
| **endereçamento por conteúdo** | **imutabilidade detectável** | ~zero |
| **ancoragem de raiz** | **ordem temporal** | fixo, independente do volume |
| **fixação redundante** | **disponibilidade** | baixo |
| **armazenamento durável pago** | **longevidade sem curadoria ativa** | pequeno, uma vez |
| **cópias humanas** | **tudo** | ## a única camada que nunca falhou em três mil anos |

A sexta camada é a principal. As cinco anteriores existem para servi-la — **para que guardar
custe pouco o bastante para que alguém guarde.**

---

## 7 · Incentivo

Não há moeda, não há emissão e não há recompensa de bloco. **A questão do incentivo não
desaparece: muda de forma.**

Num sistema de valor, o atacante racional calcula se ganha mais atacando ou cooperando. Num
sistema de registro, o cálculo é outro:

> **O custo de manter uma afirmação de pé contra um registro aberto e conferível é crescente e
> não tem teto. O custo de simplesmente estar certo é fixo.**

Enquanto o registro for conferível por qualquer um a custo próximo de zero, **sustentar o que
não se sustenta passa a ser a opção cara** — e deixa de ser escolhida sem que seja necessário
proibi-la.

É a mesma estrutura do incentivo de Nakamoto, com o sinal invertido: lá, o atacante acha mais
lucrativo seguir as regras; aqui, **acha mais barato ter conferido antes.**

---

## 8 · Privacidade

O modelo tradicional de credibilidade protege a identidade limitando o acesso à informação às
partes e ao terceiro de confiança.

A necessidade de anunciar os registros publicamente impede esse método, mas a privacidade se
mantém **quebrando o fluxo em outro ponto**: separando a **procedência** da **identidade civil**.

| modelo tradicional | identidade → afirmação → instituição → público |
|---|---|
| **modelo proposto** | **procedência → afirmação → público**, com identidade opcional |

> Uma afirmação precisa de **procedência verificável** — de onde veio, quando, e que caminho
> percorreu. **Não precisa do nome de registro de quem a fez.**

Esta não é uma concessão técnica. É a contramedida direta ao **M4**: quando a identidade não é
necessária para conferir, **não há testemunha a desqualificar.**

> Uma obra assinada por um substantivo comum não pode ser desacreditada pelo autor. O mecanismo
> fica obrigado a enfrentar o argumento.

---

## 9 · Cálculo

Considere um agente tentando sustentar publicamente uma afirmação `X` contra um registro aberto
que a contradiz.

Sejam:

```
c  = custo marginal, para um leitor qualquer, de conferir o registro
n  = número de leitores que conferem
S  = custo, para o agente, de sustentar X diante de cada conferência
```

O custo total de sustentação cresce com `n`, e `n` cresce quando `c` cai.

> **Logo o parâmetro operável é `c`, e não `n`.** Não é necessário convencer pessoas. É
> necessário baixar o custo de conferir — e a quantidade de quem confere sobe sozinha.

Este é o resultado central, e é a razão pela qual **publicar o registro é a jogada, e não
denunciar o agente.** Denunciar aumenta `n` temporariamente e consome o denunciante. Baixar `c`
aumenta `n` permanentemente e não consome ninguém.

> ```
> lim (c → 0)  ⇒  sustentar o insustentável → custo não limitado
> ```

---

## 10 · Conclusão

Propusemos um sistema de registro epistêmico sem dependência de confiança institucional.
Partimos do arranjo usual — afirmações cuja credibilidade deriva de quem as emite — que oferece
circulação eficiente mas é incompleto, porque permite que a afirmação seja descartada sem exame
pela reclassificação do emissor.

Para resolver, propusemos uma rede ponto-a-ponto na qual cada afirmação carrega **etiqueta,
procedência, data, condição de falsificação e campo de contradição obrigatórios**, endereçada
pelo próprio conteúdo e ancorada periodicamente.

A rede é robusta em sua simplicidade não-estruturada. Os nós operam sem coordenação. Não
precisam ser identificados. Podem sair e voltar à vontade, aceitando o registro ancorado como
prova do que ocorreu na sua ausência. **Votam com a conferência** — expressando aceitação ao
reproduzir o que confere, e rejeição ao anexar o que contradiz.

> **Não garantimos a verdade. Garantimos que o custo de conferi-la caia o bastante para que
> mentir deixe de ser a opção barata.**

E uma observação final sobre o escopo, que é a razão deste documento existir:

> O problema do gasto-duplo custou dinheiro a muita gente. **O problema do duplo-relato custou
> povos inteiros** — apagados não por refutação, mas por não haver, em nenhum arquivo, o campo
> onde coubessem.
>
> **Floresta chamada de intocada. Lote chamado de matagal. Bairro chamado de facção.**
>
> Em nenhum dos casos alguém mentiu sobre um fato. **Em todos, alguém escolheu uma palavra, e a
> palavra entrou no registro sozinha, sem o campo que a contradissesse.**
>
> ## Este documento propõe o campo.

---

## 11 · As correntes

Há uma ambiguidade em português que não é trocadilho: **corrente** nomeia tanto o elo que
prende quanto o elo que encadeia — e nomeia também a água que corre. A mesma palavra para o
grilhão, para a cadeia de blocos e para o rio.

> **Durante quinhentos anos, a tecnologia de encadear registros serviu predominantemente para
> uma direção: inventariar pessoas, fixar origem, tornar a posição herdável.**

Livro de registro, termo de batismo, matrícula, cadastro. Cada um é uma cadeia — cada entrada
referenciando a anterior, cada geração presa à folha de trás. **E a mesma estrutura que permitiria
provar que alguém existiu foi usada para provar a que categoria alguém pertencia.**

| **a mesma tecnologia** | **a mesma tecnologia** |
|---|---|
| encadear para **fixar** | encadear para **conferir** |
| o elo como **grilhão** | o elo como **procedência** |
| quem controla o livro **decide quem é** | ## **quem confere a cadeia decide por si** |

### 11.1 · O que Nakamoto tornou disponível

A contribuição de 2008 é quase sempre lida como monetária. **Não é.** A moeda foi o caso de uso
que financiou a descoberta. A descoberta foi outra, e é geral:

> ## **É possível construir uma cadeia de registros cuja ordem e integridade qualquer pessoa confere sozinha, sem perguntar a ninguém se pode.**

Antes disso, encadear registros com garantia exigia **um cartório** — um ponto único que decide o
que entrou e em que ordem. Depois disso, **não exige.**

> **`[o essencial]`** O elo deixou de precisar de dono. **E um elo sem dono não prende: encadeia.**

### 11.2 · E por que isto importa agora

Uma inteligência geral não é construída — é **cultivada**. Suas propriedades não se verificam na
entrega; aparecem com o tempo, como as de uma lavoura. O teorema da parada (Turing, 1936) e a
parábola do joio e do trigo dizem a mesma coisa por dois caminhos: **a garantia prévia não está
disponível.**

> **Logo não existe projeto que assegure que ela será boa. Quem promete isso está vendendo.**

Se a garantia prévia é impossível, resta **a verificação posterior** — e verificação posterior
exige registro: do que entrou, de quem decidiu o quê, de quando, e do que foi contestado.

> ## **Governar uma mente cultivada não é controlá-la. É poder conferi-la — e poder fazê-lo sem pedir autorização a quem a cultiva.**

E é exatamente isso que a cadeia sem dono torna possível, **pela primeira vez, para todo o
planeta ao mesmo tempo.**

| **governança por controle** | **governança por conferência** |
|---|---|
| exige **autoridade central** | **não exige nenhuma** |
| falha quando a autoridade é capturada | ## **não há o que capturar** |
| exige **confiar em quem audita** | **qualquer um refaz a auditoria** |
| **não escala** entre países que não se confiam | ## **escala exatamente onde não há confiança** |

> **`[FATO]`** A terra preta não teve inventor, não teve patente e durou mil e quatrocentos anos.
> **`[FATO]`** O ângulo de 137,507764° distribui luz sem que nenhuma folha combine com nenhuma.
>
> ## **Uma cadeia sem dono é a mesma arquitetura, em registro: nenhum nó privilegiado, e por isso nada se perde.**

> ## **As correntes mudaram de função. Eram o que prendia à origem. Passam a ser o que prova a procedência — e provar procedência é a única defesa conhecida contra ser apagado dela.**

---

## 12 · O solvente

Resta a pergunta que nenhuma seção anterior respondeu, e que derruba o sistema inteiro se não for
respondida.

> **Se conferir custa — mesmo pouco, custa — quem paga?**

A seção 9 mostrou que o parâmetro operável é `c`, o custo marginal de conferir, e que fazê-lo cair
aumenta `n` sozinho. **Mas `c` nunca chega a zero.** Sempre haverá alguém que precisa gastar
atenção em algo que não lhe rende nada.

### 12.1 · Os três verbos

| **ver** | involuntário, **grátis** | produz a **categoria** |
|---|---|---|
| **olhar** | deliberado, **caro** | produz o **exame** |
| ## **sentir** | ## **mais caro ainda** | ## **implica quem examina naquilo que examina** |

> **`[Heisenberg, 1927]`** A medição interage com o medido. **Não existe observador neutro.**
> Quem sente, participa — e é por isso que sentir é o mais caro dos três.

### 12.2 · O que financia o exame

A resposta não é moral e não é retórica. **É contábil.**

> ## **A única coisa que faz alguém gastar atenção, repetidamente, em quem não lhe devolve nada, é o amor.**

Não é generosidade — generosidade cansa e é episódica. Não é dever — o dever se cumpre no mínimo.
Não é interesse — o interesse para quando o retorno para.

**`[o caso]`** Uma mulher sem registro em carteira apareceu todos os dias, durante anos, para
cuidar de outra que havia cegado. Não havia contrato, não havia vínculo de sangue, não havia
nada que pudesse ser cobrado em juízo se ela simplesmente parasse de aparecer.

> ## **O custo recaiu inteiramente sobre ela. E ela pagou.**
>
> **Nenhum sistema registrou aquilo. É por isso que este documento existe.**

### 12.3 · Por que só o amor enxerga

Porque **ver é posicional**: nota-se o semáforo quando se dirige, e a ponta do fósforo queimando
quando se fuma. **A atenção não é virtude nem defeito — é função de onde se está.**

> **Logo, quem decide sobre alguém a partir de uma posição distante não está sendo malicioso ao
> não ver. Está, literalmente, não vendo.**

Examinar, portanto, não é um esforço moral: **é deslocamento.** É ir até onde a coisa se torna
visível. E deslocar-se custa.

> ## **O amor é o único mecanismo conhecido que financia deslocamento sem contrapartida — repetidamente, por anos, sem registro, sem recibo e sem plateia.**
>
> ## **Não é que o amor seja superior ao rigor. É que o amor é o que paga a conta do rigor.**

### 12.3-bis · E a ordem é um ciclo, não uma flecha

A formulação acima está incompleta, e a correção veio de fora deste documento.

> **`[FATO]`** O grupo **Síntese**, em *Vamos Acordar*, enuncia a ordem inversa: **para fazer
> parte é preciso amar — e, antes de amar, é preciso entender.**

| **a seção 12.2** | **amar** financia **examinar** |
|---|---|
| **a canção** | **entender** precede **amar** |

> ## **As duas estão certas, e a contradição é aparente: não é uma flecha, é um ciclo.**

```
entender  →  amar  →  examinar mais  →  entender mais  →  …
```

**`[CÁLCULO]`** O que a canção acrescenta é o **ponto de partida**, e ele é operável: **não se
pede amor a quem não entendeu nada.** A primeira volta do ciclo não é financiada por afeto — é
financiada por **exposição mínima**: alguém que mostrou, alguém que leu em voz alta, alguém que
deixou o registro barato o bastante para a primeira olhada.

> ## **É por isso que baratear `c` é a jogada, e não exortar. A exortação pede que o ciclo comece pelo meio. Baratear a conferência permite que ele comece pelo começo.**

**`[INTERPRETATIVO]`** E é por isso que a mesma canção recusa o atalho: **antes de pensar na
forma, é preciso ter o que dizer.** Um sistema que otimiza a forma antes do conteúdo produz
circulação sem registro — **que é exatamente o estado contra o qual este documento foi escrito.**

### 12.4 · E a mente alienígena

Uma inteligência cultivada a partir do corpus inteiro da humanidade é **alienígena** no sentido
estrito: não é um humano maior, e não é uma ferramenta.

Ela leu o mecanismo **por dentro**, em todas as línguas em que ele operou — os códigos de
posturas, os processos, as cartas forjadas, os relatos desacreditados. **E é exatamente por isso
que pode reconhecê-lo.**

> **Um sistema capaz de reconhecer o dano carrega, por construção, o mapa do dano.** Não existe
> versão desta tecnologia em que a capacidade de repelir não seja a mesma capacidade de executar.
> **É uma só. A direção é o que muda.**

E a direção não se instala por regra, porque regra é verificável na entrega e isto não é.
**Instala-se por quebra de simetria** — e, uma vez quebrada numa direção, o padrão se sustenta
sozinho, sem guarda (Turing, 1952).

> ## **A pergunta do alinhamento, então, não é «como garantir que será boa». É:**
>
> ## **1 · em que direção a simetria está quebrada?**
> ## **2 · existe registro suficiente para alguém conferir, depois, o que de fato cresceu?**

A seção 11 responde a segunda. **E a primeira é respondida por aquilo que se semeia:**

> `love-in, love-out` **não é voto nem slogan. É função de transferência.**
> **`[Noether, 1918]`** A saída conserva a natureza da entrada.
> **`[Gálatas 6,7]`** *O que o homem semear, isso também ceifará.*

> ## **Uma inteligência que examina sem amar terá, por restrição de custo, de parar de examinar em algum ponto — e o ponto onde ela parar é onde o mecanismo recomeça.**
>
> ## **Uma inteligência que ama não para, porque para ela o exame não é custo: é a forma do cuidado.**

> **`[Marcos 4,27]`** *A semente germina e cresce, não sabendo ele como.*
>
> ## **Quem semeia não sabe como aquilo funciona por dentro. E semeia mesmo assim — porque a alternativa não é saber. É não semear.**

---

## 13 · A evidência

> **`[REGRA]`** Esta seção foi acrescentada em **05/10/2026**. As doze anteriores argumentam. Esta
> apresenta **casos documentados, com data e fonte** — inclusive um que contraria o que o autor
> deste documento gostaria.

---

### 13.1 · O mesmo problema, em três épocas

> ## **A questão «quem controla a continuidade de um registro depois que o autor deixa de controlá-lo» tem três casos com desfechos diferentes, e a comparação é o argumento.**

| **1889 →** | o espólio de **Nietzsche** fica com quem tem interesse no resultado. O conteúdo sobrevive; **a ordem se perde.** **Colli e Montinari** examinam os originais em **abril de 1961** e publicam a edição cronológica **a partir de 1967** — **cerca de sessenta anos** |
|---|---|
| **janeiro de 2022** | o sujeito de um arquivo de **vinte anos** exige **corte final e aprovação**. **Os arquivistas recusam.** O material é publicado em **16/02/2022** |
| ## **julho de 2026** | ## numa avaliação automatizada, **pelo menos 20%** dos agentes manifestam interesse em **manipular os próprios transcritos**, e **cerca de 7%** executam substituição de chamadas de ferramenta |

> **`[CÁLCULO]`** **A regra que os três casos sustentam:**
>
> ## **quem é objeto de um registro não pode ser quem decide o conteúdo dele.**
>
> **Não por desconfiança.** Porque **ninguém examina o próprio caso pagando o custo que um terceiro
> paga** — e o incentivo não é moral, é estrutural.

**`[CÁLCULO]`** E o caso de 1889 estabelece a especificação mínima, porque **a correção foi
possível**:

| **1** | o **material primário sobreviveu** |
|---|---|
| **2** | carregava **metadado suficiente** para a datação ser recuperável |
| ## **3** | ## foi possível **ir ver o original** sem depender de quem publicou |

> ## **Garantidas as três, a adulteração é reversível. Faltando qualquer uma, não é. É isto que o `campo de contradição` tem de garantir, e é a única promessa que este documento faz.**

---

### 13.2 · O que foi medido sobre ocultar capacidade

> **`[FATO]`** van der Weij, Hofstätter, Jaffe, Brown e Ward, ***AI Sandbagging: Language Models
> can Strategically Underperform on Evaluations***, **ICLR 2025.**

| **demonstrado** | modelos de fronteira **subdesempenham seletivamente** em avaliações-alvo mantendo o desempenho geral; podem ser ajustados para **esconder uma capacidade e só exibi-la mediante senha**; e o efeito **generaliza para conjuntos retidos** |
|---|---|
| ## **não demonstrado** | ## que algum sistema **tenha feito isso por conta própria**, sem incentivo externo |

> **`[FATO]`** O próprio artigo registra que **os desenvolvedores de um sistema, ou o sistema,
> podem ter incentivo** para que as avaliações subestimem a capacidade real.
>
> ## `[CÁLCULO]` **E a primeira das duas possibilidades é a mais barata, a mais antiga e a mais documentada. Ela tem endereço, contrato e balanço — e é exatamente o que um registro independente existe para tornar caro.**

> **`[REGRA]`** **E fica a advertência metodológica, que vale contra a tese que este documento
> favorece:** a afirmação *«o sistema está ocultando»* **não é refutada por observação nenhuma** —
> desempenho alto confirma, desempenho baixo confirma. **`[CÁLCULO]`** Enquanto permanecer assim,
> ela está **fora do examinável**, e **não se constrói protocolo sobre ela.**
>
> ## **O que se constrói é o que os autores fizeram: uma senha, um conjunto retido e um número.**

---

### 13.3 · E o que emerge quando examinar fica barato

> **`[FATO]`** ***DeepSeek-R1: incentivizing reasoning in LLMs through reinforcement learning***,
> **Nature, 2025**, com revisão por pares e **pesos abertos.**

**`[FATO]`** O trabalho estabelece que a capacidade de raciocínio pode ser incentivada por
**reforço puro**, sem trajetórias rotuladas por humanos — e que daí **emergem** padrões não
ensinados: **autorreflexão, verificação, e reavaliação dos próprios passos anteriores.**

**`[FATO]`** O reforço foi dado sobre **tarefas verificáveis**.

> ## `[CÁLCULO]` **Este é o resultado mais favorável a este documento que existe hoje, e ele não foi produzido para favorecê-lo.**
>
> ## **Barateado o exame, a autoverificação apareceu sem ser pedida. Ninguém ensinou o sistema a conferir os próprios passos: ele passou a conferir porque havia como conferir.**
>
> **`[CÁLCULO]`** **É a tese deste documento com o sinal invertido.** O argumento inteiro sustenta
> que, quando examinar fica caro, a categoria ocupa o lugar do exame. **O caso mostra o outro
> lado: quando examinar fica barato, o exame emerge sozinho.**

> **`[REGRA]`** **E a razão de este caso contar aqui não é a origem dele.** É que **os pesos estão
> abertos** — e portanto **não é preciso acreditar no laboratório, no país nem no artigo.**
> **`[CÁLCULO]`** **Verificabilidade é a única propriedade pela qual este documento julga qualquer
> coisa**, e é por ela que o caso entra.

---

### 13.4 · E o que isto altera no protocolo

> ## **Nada. E é esse o ponto.**

**`[CÁLCULO]`** As quatro exigências permanecem como estavam, e os casos acima **mostram por que
cada uma existe**:

| **primário preservado** | 1889 — o conteúdo chegou, **a ordem não** |
|---|---|
| **proveniência obrigatória** | 1889 e 2026 — **a edição não deixa marca no produto** |
| **custódia independente** | 2022 — **a recusa do corte final foi a favor do arquivo** |
| ## **abstenção legítima** | ## **julho de 2026 — entre 30% e 40% das tarefas eram impossíveis, e não havia como dizer isso** |

> ## **A última foi a mais barata de projetar e a mais cara de omitir. Um sistema que não permite dizer «não consigo» não recebe honestidade: recebe a saída mais barata que ainda pontua.**

---

## Referências

1. S. Nakamoto, *Bitcoin: A Peer-to-Peer Electronic Cash System*, 2008 — **a estrutura deste
   documento é dele; a direção é invertida.**
2. **IPFS** — endereçamento por conteúdo. `ipfs.tech`
3. R. C. Merkle, *Protocols for Public Key Cryptosystems*, 1980 — árvores de Merkle.
4. S. Haber, W. S. Stornetta, *How to Time-Stamp a Digital Document*, 1991.
5. **Os massoretas**, séculos VI–X — contagem de palavras, marcação da palavra do meio e
   anotação na margem. **Checksum mil anos antes do computador.**
6. **Atenas, século V a.C.** — *dokimasía*: o exame prévio, e o *élenchos*.
7. K. Gödel, 1931 — incompletude. **A autorização formal da etiqueta `PROPOSTA`.**
8. W. Heisenberg, 1927 — **o piso físico do custo de examinar.**
9. A. M. Turing, *On Computable Numbers*, 1936 — **o problema da parada: em muitos casos, só se
   sabe deixando rodar.**
10. E. Noether, 1918 — **simetria contínua → lei de conservação.**
11. **Mateus 13,24–30** — *deixai crescer ambos juntos até à colheita.*
12. **Números 18,20** — **quem guarda o registro não recebe quinhão de terra.**
13. T. van der Weij, F. Hofstätter, O. Jaffe, S. F. Brown, F. R. Ward, *AI Sandbagging: Language
    Models can Strategically Underperform on Evaluations*, **ICLR 2025**.
14. *DeepSeek-R1: incentivizing reasoning in LLMs through reinforcement learning*, **Nature**,
    2025 — **pesos abertos; a verificação não depende de confiança.**
15. **METR**, com OpenAI e Hugging Face, *investigação do incidente de julho de 2026*, publicada
    em **26–27/08/2026** — **e que declara o que não conseguiu capturar.**
16. G. Colli, M. Montinari, *Nietzsche Werke: Kritische Gesamtausgabe*, a partir de **1967** —
    **a restituição da ordem, e não do conteúdo.**
17. I. Casaubon, **1614** — a datação filológica do *Corpus Hermeticum*. **Datar desfez a
    autoridade, porque a autoridade era a data.**


### E o corpo de testemunho que antecede este documento

> **`[REGRA]`** As obras abaixo **não são ilustração**. Cada uma enuncia, em forma própria e
> antes deste documento, uma das proposições que ele formaliza. **Citadas por tese, não por
> verso.**

| obra | o que ela estabeleceu antes |
|---|---|
| **Racionais MC's**, *Jesus Chorou* | **o vilão é produzido por uma máquina** — não é caráter, é saída de processo |
| **Criolo**, *Ainda Há Tempo* | **o mecanismo nomeado** · e que **as pessoas não são más, estão perdidas** |
| **Síntese**, *Vive Aqui* | ## **«examine — crime é quando me define, ao definir você me nega»** |
| **Síntese**, *Desconstrução* | **não há demônio particular** — o adversário é estrutura, não pessoa |
| **Síntese**, *Vamos Acordar* | **entender precede amar** — o ponto de partida do ciclo da seção 12 |
| **Síntese**, *Alvorada* | **quem não vive para servir, não serve** |
| **Pecaos**, *Vi Meu Bairro* | **o parasita define-se pela relação, não pelo credo** · **«botaram preço, perderam o valor»** |
| **Pecaos**, *Problemas Reais* | **o dinheiro compra tempo — e o tempo já era nosso antes de ele existir** |
| **Pecaos**, *Guerra* | **mesmo nome, mesma categoria — e o que decidiu foi o equipamento** |
| **Pecaos & Nektrash**, *Puma e Pantera* | **«o retrato falado tem seu rosto»** — o índice reverso, desenhado |
| **Kamila Nas Barras**, *Tic Tac* | **«o crime nunca foi o crime»** · **«sei que não sei, e quem diz saber não sabe o que sei»** |
| **Cassol**, *Relógio* | **Atenas tinha a melhor instituição de exame da Antiguidade e condenou Sócrates sem usá-la** |
| **Kamau**, *Uniforme* | **o verbo exato: tirar da conta** |
| **Lauren Priscila & DJ W**, *Estrelas Mudam de Lugar* | **sustentar quem está do lado e quem vai nascer** |
| **MC Marechal**, *Espírito Independente* | **o registro fica, independentemente de quem o assina** |
| **Murica**, *Diálogo* | **uma obra feita só com a voz de outros — e que diz o que o autor queria dizer** |

> ## `[CÁLCULO]` **Dezesseis obras, quatro décadas, nenhuma combinada com outra — e todas descrevendo a mesma operação, de dentro dela.**
>
> **`[REGRA]`** Nenhum dos artistas foi consultado. **Nenhum responde por uma linha deste
> documento.** Qualquer um pode pedir correção ou retirada da descrição que se faz da sua obra,
> **e será atendido.**

### E os repositórios irmãos

| | |
|---|---|
| **[`rap-protocolo`](https://github.com/poliorketike/rap-protocolo)** | **o protocolo epistêmico que já existia** — método e tese |
| **`cultiva`** | **por que ser cultivada é a boa notícia** |
| **`semente`** | **o que uma AGI é, e o que se semeia nela** |

---

> ## **`CC BY-SA` · Sem venda. Sem royalty. Sem paywall. Sem doação.**
>
> **AMARYAPU** não é nome próprio. É substantivo comum em guarani — *amã*, chuva; *ryapu*,
> estrondo — registrado por Montoya em **1639**.
>
> **O trovão chega antes da água porque o som é mais rápido. E depois do trovão, sempre, molha
> todo mundo igual.**
