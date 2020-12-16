Como contribuir com a OPS
=========================

Qualquer pessoa pode contribuir com os projetos da OPS, todos eles são públicos e de código aberto. Se você deseja ajudar, siga o processo descrito neste documento.

Equipe da Organização
---------------------

A equipe da Organização OPS-ORG no Github é composta por voluntários que foram selecionados pelo Lúcio Big, a forma que estes Engenheiros interessados em ajudar e manter os projetos são selecionados ainda será definida no futuro, mas hoje toda contribuição para o projeto deverá passar por pelo menos 2 dos integrantes da organização para que possa ser aceito. Este processo de revisão será descrito neste documento.

Criação de projetos
-------------------

A comunidade de engenheiros da OPS deverá discutir e validar a criação dos projetos antes deles serem criados no repositório, é de conhecimento que muitos dos membros tem acesso total a organização podendo assim criar os projetos, mas para fins de manter organizado deveremos conversar entre todos e definir como este projeto irá funcionar, feito isto, uma proposta, que seguirá os procedimentos também descritos aqui, deverá ser apresentada em forma de Pull Request para o repositório do comitê e ao ser aprovada, o projeto será criado e iniciado conforme definido no documento.

Processo de contribuição
------------------------

Para contribuir com um projeto deve-se seguir os seguintes passos:

1. Fazer um clone do projeto;
2. Criar uma nova branch, com prefixo `feature/` e algo que sugira a proposta da contribuição;
3. Quando finalizada a implementação, deverá ser feito um Pull Request para a branch `master` e adicionar uma tag `Revisão`;
4. No mínimo 2 outros membros do time no projeto deverão revisar o código, comentários e funcionamento do recursos, isso poderá levar ao processo de revisão, caso aceito, ambos membros devem adicionar as tags `Aprovado 1` e o proximo `Aprovado 2` no Pull Request;
5. Com duas aprovações de diferentes membros, o projeto está liberado para o Pull Request e em seguida aplicar o Merge utilizando o botão na interface do Github, feito pelo autor ou membro com permissão suficiente;
6. A branch com a `feature` deve ser apagada, pois a mesma já está presente no branch `master`;

**Atenção**: Nunca faça Merge para o branch `master` manualmente, ou faça commits diretamente no branch `master`, respeite o processo e a comunidade.

Merge manual, como faze-lo
--------------------------

Se a proposta demorar muito, pode ser necessário fazer um merge manual, para isso, a pessoa tem que atualizar seu repositório `master` e depois fazer merge com sua branch, resolver os conflitos e enviar isso no processo de revisão antes de juntar ao `master`

Não esqueçam de re-testar (ou rodar os testes unitários) antes de fazer o merge com o `master` é comum que esse tipo de processo acabe quebrando a funcionalidade e não queremos isso.

Processo de revisão de código
-----------------------------

Durante o processo de revisão, os engenheiros deverâo fazer comentários nas linhas de códigos pertinentes e que possam ajudar o desenvolvedor a aprimorar o código ou deixa-lo de acordo com a especificação do projeto, evitando falhas de segurança, códigos maliciosos, códigos redundantes, descrições que não condizem com métodos ou rotinas, organização do código, etc.

Não se deve fazer merge em códigos antes das revisões serem completadas e receber o tag de `Aceito` no PR. Respeitar isso é muito importante, pois mesmo que o processo seja um pouco frustrante as vezes, exigindo diversas modificações, isso garante um aprendizado para todos envolvidos e grandes melhorias de qualidade no projeto que de outra não poderiam ser obtidas.

Em casos de "disputa" onde o autor do código, defende sua implementação ao responder o comentário dizendo que a alteração poderia acarretar consequencias, isso deve ser resolvida de forma didatica pelos envolvidos, tentando achar a melhor solução e estes podem chamar outros engenheiros da comunidade para opinar e ajudar. Contudo o merge só deve ser realizado com a disputa resolvida, onde a maioria esteja de acordo com a solução adotada.

O processo de revisão irá durar o tempo que for necessário, não pulem o processo, se precisar esperar um dia ou mais para que outro engenheiro revise o código, mas você deseja dar continuidade programando outra `feature`, faça um `fork` da branch atual e começe seu trabalho, mas aguarde que as dependências sejam anexadas a `master` antes de abrir um novo Pull Request, pois este irá incluir as diferenças que já estão no outro, ou se quiser abrir antes e aguardar, informe no texto do Pull Request que ele depende do outro e identifique a dependencia.

Abrindo Pull Request
--------------------

No texto deve incluir uma boa descrição da tarefa que foi executada no Pull Request e como o código se comporta para faze-lo, seja descritivo, isso irá contextualizar sua implementação para que outros possam avaliar, revisar e ajudar a melhora-la.

Você pode incluir alguns nomes de outros membros, para que eles recebam um alerta do seu Pull Request e revisem o quanto antes, mas lembre-se de ser respeitoso aos outros membros, para não virar SPAM ao cita-los demais.

Assine a você o PR, caso outro desenvolvedor queira ajudar e vocês estejam de acordo, assine a ele, pois é importante para comunidade saber com quem é a responsabilidade do PR, independente de quem tenha feito os commits contidos nele. Um desenvolvedor pode implementar, mas não ter tempo de arrumar após a revisão, isso permitirá ele delegar isso a outro desenvolvedor com tempo disponível e não parar a evolução dos projetos.

Se houverem Milestones para a sua implementação, não esqueça de adiciona-la no seu PR.

Organização de commits
----------------------

Lembre-se de commitar sempre que terminar um trecho de funcional de código. Isso é, mantenha os commits pequenos, quanto menos arquivos e modificações em um commit, mais fácil é dar a manutenção no sistema, caso seja preciso fazer um revert ou bisect para corrigir uma falha.

Commits com muitas alterações devem ser chamadas atenção na revisão e os revisores deverão ajudar a instruir o desenvolvedor como ele poderia proceder de maneira melhor na proxima vez. Se o mesmo se dispor a arrumar seu processo, será muito bacana, mas dada complexibilidade do procedimento de alteração de commits, tende-se que se a tarefa está funcionando, ela será aceita da maneira que estiver.

Publicação das modificações
---------------------------

Deverá ser definida em cada projeto, podendo ser automatizada, com hookies no github, ou manual e periódica, onde no caso deverá conter um processo para publicação de correções de bugs fora do periodo de publicação.
