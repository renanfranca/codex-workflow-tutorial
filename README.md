# Tutorial: um ciclo de trabalho com Codex

Vitão, você vai especificar, planejar, implementar com testes, commitar e conferir
uma saudação em Python, sem dependências externas. A meta é **até cinco minutos
de leitura e ações**, excluindo esperas do Codex, downloads e preparação de
ferramentas ausentes. Esse tempo ainda precisa ser medido na extensão.

Abra uma **pasta vazia** no VS Code do Windows e a extensão Codex autenticada.
Com **Plan desligado**, envie somente:

```text
https://github.com/renanfranca/codex-workflow-tutorial
```

Se ele perguntar o que fazer com o link, responda **“Siga este tutorial”**.
O Codex deve executar a preparação descrita abaixo e entregar `GUIA.md` na pasta
aberta. Depois, acompanhe o roteiro local. Você controla as trocas de chat, modo
e modelo; o Codex não deve fazê-las por você.

<!-- GUIA-INICIO -->

## Antes de começar

Confira as seis skills no seletor ao digitar `$` em um novo chat. Se faltar alguma,
peça ao chat de preparação para verificar a descoberta; reinicie o Codex se
necessário. Arquivos copiados provam **instalação**; aparecer no seletor/contexto
prova **descoberta**; leitura de `SKILL.md` e execução do fluxo evidenciam
**ativação**. Uma declaração isolada não comprova ativação.

Nos seletores junto à caixa de mensagem, escolha **Plan**, modelo e esforço
indicados em cada etapa. `xhigh` pode aparecer como **Extra High**, `medium` como
**Medium**, `high` como **High**. Se Sol ou Luna não estiver disponível,
informe a limitação ao Codex antes de continuar. Mantenha a mesma pasta em todos
os chats.

## 1. Especificar

**Novo chat · Plan · Sol xhigh.** Cole:

```text
Use $specify-issue. Leia GUIA.md e as instruções do repositório; inspecione os arquivos existentes. Proponha .agent/specifications/saudacao-cli.md em inglês: saudacao.py, Python padrão, um nome opcional não vazio; sem argumento, “Olá, mundo!”; com Codex, “Olá, Codex!”. Cada resultado ocupa uma linha, termina com quebra de linha, sai com código 0 e stderr vazio. Argumentos extras ou vazios ficam fora deste ciclo. Ainda não grave nem implemente.
```

## 2. Gravar a especificação

**Mesmo chat · desligue Plan · mantenha Sol xhigh.** Leia a proposta; estando de
acordo, cole:

```text
Aprovo a proposta apresentada para .agent/specifications/saudacao-cli.md. Grave e valide somente essa especificação, em inglês. Não implemente nem altere o Git.
```

## 3. Planejar

**Novo chat · Plan · Sol xhigh.** Cole:

```text
Leia GUIA.md, .agent/specifications/saudacao-cli.md e os arquivos existentes. Crie um ExecPlan com $plan-behavioral-acceptance: associe cada requisito à fonte, exemplo, verificação e evidência esperada. Use o Python registrado em GUIA.md e comandos exatos. Planeje testes pela CLI com unittest, um comportamento por ciclo, falha antes do código, suíte verde e as duas saudações. Inclua revisão estrutural após tudo verde. Separe expectativa correta de prova suficiente; registre lacunas. Entregue o plano completo, autossuficiente e compacto, em um único bloco md, sem gravar ou executar.
```

Copie **todo o bloco do plano**, sem resumos. Ignore um eventual botão para
implementar neste chat: a próxima etapa usa outro chat.

## 4. Implementar

**Novo chat · Plan desligado · Sol medium.** Cole o prompt e, logo depois, o bloco
completo copiado:

```text
Leia GUIA.md e .agent/specifications/saudacao-cli.md. Execute o ExecPlan completo colado abaixo. Grave-o em EXECPLAN.md antes da implementação, preservando evidências anteriores pertinentes. Faça TDD comportamental autônomo: um comportamento por ciclo, suíte relevante falhando antes do código e passando depois; confira as duas saudações pela CLI. Depois de concluir o comportamento com tudo verde, revise o desenho estrutural preservando o contrato. Confirme as skills efetivamente usadas. Registre em EXECPLAN.md comandos, códigos de saída, motivo do red, asserções e green, saudações, revisão e lacunas por critério; atualize nos marcos e na entrega. Não commite.
```

O pedido de ExecPlan favorece a seleção implícita de `implement-execplan`; o de
TDD e revisão favorece `tdd-behavior-autonomous-quiet` e `refactor-design`.
Seleção implícita depende da descrição da skill, não é garantia. Confira a
ativação pelas mensagens e leituras de arquivos. Se faltar, no chat correspondente:

```text
Leia GUIA.md, .agent/specifications/saudacao-cli.md e EXECPLAN.md, se existir. Use $implement-execplan no plano; $tdd-behavior-autonomous-quiet na implementação; $refactor-design apenas após comportamento completo, suíte e CLI verdes. Retome a etapa atual e registre as evidências, sem inventar resultados anteriores.
```

A revisão pode concluir **No action**, com justificativa. Se o código tiver sido
escrito antes dos testes, registre a falha de processo: passar testes depois não
prova TDD; não fabrique um red nem apague trabalho para simulá-lo.

## 5. Commitar

**Novo chat · Plan desligado · Luna high.** Cole:

```text
Leia EXECPLAN.md e inspecione status, histórico e diff deste repositório. Use $commit-the-changes para commitar apenas o trabalho do ciclo. Sem histórico, use Conventional Commits em inglês. Preserve alterações alheias e não faça push. Informe hash e assunto; confirme os arquivos incluídos.
```

## 6. Conferir

**Volte ao chat da etapa 3 · Plan · Sol xhigh.** Cole:

```text
Releia GUIA.md, .agent/specifications/saudacao-cli.md, EXECPLAN.md, saudacao.py e os testes. Compare requisitos, implementação e evidências; inspecione o commit com Git. Verifique separadamente expectativas e suficiência das provas: falhas anteriores ao código, suíte passando, duas saudações, revisão estrutural e hash/conteúdo do commit. Execute verificações de leitura permitidas; não edite. Aponte pendências com fonte e impacto, sem considerar prova ausente como aprovação.
```

## 7. Corrigir quando necessário

No mesmo chat, **Plan · Sol xhigh**:

```text
Leia .agent/specifications/saudacao-cli.md, EXECPLAN.md, saudacao.py e os testes. Use $plan-behavioral-acceptance para planejar as pendências desta conferência sem ampliar o contrato. Inclua as pendências no ExecPlan completo, com fontes, verificações e evidências; preserve o histórico útil. Não implemente. Se a especificação precisar de decisão, volte à etapa 1. Entregue um único bloco md para outro chat.
```

Copie o plano e repita **4 → 5 → 6**. Sem pendências, prossiga.

## 8. Reiniciar com uma melhoria

**Novo chat · Plan · Sol xhigh.** Este prompt inicia o próximo ciclo:

```text
Leia GUIA.md, .agent/specifications/saudacao-cli.md, EXECPLAN.md, saudacao.py e os testes. Use $specify-issue para propor a revisão da mesma especificação: adicionar --maiusculas, preservando as saudações atuais sem a opção. Com --maiusculas, exigir “OLÁ, MUNDO!”; com --maiusculas Codex, “OLÁ, CODEX!”, mantendo quebra de linha, código 0 e stderr vazio. Planeje a mudança de contrato; não grave nem implemente ainda. Após aprovação e gravação, seguirei a etapa 3 com $plan-behavioral-acceptance para obter o próximo ExecPlan.
```

<!-- GUIA-FIM -->

## Preparação: instruções para o Codex

<details>
<summary>Execute esta preparação ao receber a URL ou “Siga este tutorial”</summary>

Leia este README integralmente, inclusive esta seção. A solicitação é preparar o
ambiente na pasta aberta e conduzir o usuário até a etapa 1. Não execute o ciclo
inteiro nem gere a solução, testes ou especificação antecipadamente.

### Conferir o ambiente

1. Identifique a raiz aberta, instruções aplicáveis, shell e sistema do processo
   que executa suas ferramentas. Diferencie **Windows nativo** de **WSL** por
   evidência do processo, como plataforma Python, kernel e `WSL_DISTRO_NAME`.
   Não deduza pelo terminal integrado do VS Code. Resolva a pasta pessoal nesse
   mesmo ambiente; não misture caminhos e instalações Windows/WSL.
2. Confira `git --version`. Localize Python 3 funcionando: no Windows, tente
   `py -3 --version` e `python --version`; no WSL, `python3 --version`. Rejeite
   atalhos que apenas abrem a Microsoft Store. Confirme `unittest` e `venv` da
   biblioteca padrão. Use UTF-8 explicitamente nos comandos e subprocessos do
   exercício, por exemplo `py -3 -X utf8` ou `python3 -X utf8`.
3. Inspecione a pasta e `git rev-parse --show-toplevel`. Em pasta vazia fora de
   outro repositório, faça `git init -b main`. Se estiver dentro de um repositório
   pai, não inicialize por cima dele: explique e peça outra pasta. Se este
   exercício já existir, reconheça a etapa pelos arquivos e preserve tudo,
   inclusive código, testes, plano, especificação, index e commits. Para conteúdo
   alheio ou conflitante, esclareça o destino antes de escrever.
4. Confira `git var GIT_AUTHOR_IDENT` e `git var GIT_COMMITTER_IDENT`, sem publicar
   os valores. Se faltar autoria, solicite nome e email desejados e configure
   apenas este repositório com `git config --local user.name` e `user.email`.
   Não invente identidade nem altere configuração global.

Se faltar ferramenta, explique somente a instalação necessária e retome depois
de conferir o comando funcionando. Windows: [Git for Windows](https://gitforwindows.org/)
e [Python para Windows](https://www.python.org/downloads/windows/); feche e reabra
o VS Code após ajustar o PATH. WSL: use o gerenciador da distribuição, por
exemplo `sudo apt install git python3 python3-venv` em Ubuntu/Debian, com a
autorização exigida pelo ambiente. Não exige Node, pip, GitHub CLI ou conta GitHub
para realizar o exercício local.

### Instalar as seis skills completas

Fonte: [renanfranca/codex-skills](https://github.com/renanfranca/codex-skills),
revisão conferida **`075ea3ffb228e596bdb3b2b3ca769aad858b31cd`**.

| Diretório na fonte | Papel no ciclo |
| --- | --- |
| `specify-issue` | Proposta aprovada e especificação em inglês |
| `implement-execplan` | Estrutura, execução e manutenção do ExecPlan |
| `plan-behavioral-acceptance` | Expectativas fundamentadas, verificações e evidências |
| `tdd-behavior-autonomous-quiet` | Teste antes do código, um comportamento por ciclo |
| `refactor-design` | Revisão estrutural com comportamento completo e verde |
| `commit-the-changes` | Histórico, seleção de arquivos e commit |

Obtenha essa revisão com Git em uma pasta temporária fora do exercício. Por
exemplo: `git clone --no-checkout https://github.com/renanfranca/codex-skills.git`
e depois `git checkout --detach 075ea3ffb228e596bdb3b2b3ca769aad858b31cd` dentro
do clone temporário. Use diretório temporário novo, sem reutilizar uma pasta alheia.
Confirme `git rev-parse HEAD` antes de copiar.

Copie **cada diretório inteiro** listado acima para a pasta pessoal de descoberta
**`.agents/skills` do usuário que executa o Codex**. No Windows nativo, resolva-a
a partir do perfil Windows efetivo; no WSL, da home Linux efetiva. Preserve
`agents/`, `references/`, `scripts/` e demais arquivos presentes. Compare caminhos
relativos e hashes SHA-256 de todos os arquivos com a fonte. Não basta copiar
`SKILL.md`. Não copie o `AGENTS.md` raiz da fonte nem suas regras de memória para
o exercício; as skills individuais são independentes desse repositório.

Se uma skill já existir e for idêntica, reutilize-a. Se diferir ou estiver
incompleta, não sobrescreva: relate a diferença e peça decisão. Confira possíveis
duplicatas em escopos de projeto/usuário e configurações que desabilitem essas
skills, sem alterar configuração alheia automaticamente. Registre o resultado
individual como instalada, reutilizada ou bloqueada e a revisão da fonte.

### Entregar o guia e verificar descoberta

Crie apenas `GUIA.md` e `.gitignore`, se ausentes, além do Git e da instalação
autorizados. Em `.gitignore`, exclua `__pycache__/`, `*.py[cod]` e `.venv/`.
Não altere arquivos existentes automaticamente.

Em `GUIA.md`, escreva um título e um cabeçalho curto com ambiente detectado,
raiz do exercício, comando Python exato com UTF-8, destino/revisão e estado das
skills. Inclua os comandos exatos para executar `saudacao.py`, `saudacao.py Codex`
e `-m unittest discover -s tests -v` depois da implementação, sem executá-los
agora. Copie em seguida o trecho deste README entre `GUIA-INICIO` e `GUIA-FIM`.
Esses nomes de arquivos são relativos à raiz do exercício. Reserve `tests/` para
testes de comportamento pela CLI; nenhum arquivo de código/teste deve existir
por efeito da preparação.

Separe os estados observados: confirmar arquivos não confirma descoberta.
Peça ao Vitão abrir novo chat e verificar os seis nomes no seletor `$` ou
`/skills`, quando disponível. Se faltarem, verifique caminhos efetivos,
frontmatter, configurações e duplicatas; reinicie o Codex se necessário. Não
declare descoberta sem acesso à lista/contexto ou confirmação do usuário.
Cada chat posterior deverá carregar as skills apropriadas à sua etapa, e
confirmar uso com comportamento e leitura dos contratos correspondentes.

Finalize com: ambiente, ferramentas prontas ou pendentes, estado das seis skills,
caminho clicável de `GUIA.md` e a ação **“novo chat, Plan, Sol xhigh, etapa 1”**.
Se houver pendências, entregue a próxima ação de preparação em vez da etapa 1.
Se a execução for repetida, informe a etapa já alcançada e a próxima ação sem
recriar o exercício. Não faça commit nem publique o exercício durante a preparação.

</details>

## Fontes e validação

O modelo de descoberta e seleção está documentado em
[Build skills](https://learn.chatgpt.com/docs/build-skills). Para a plataforma,
consulte a documentação da [extensão Codex](https://learn.chatgpt.com/docs/codex/ide)
e de [Windows/WSL](https://learn.chatgpt.com/docs/windows/windows-sandbox).
As escolhas Sol/Luna e esforços acima são as configurações deste roteiro;
a disponibilidade precisa ser conferida na extensão de cada usuário.

Consulte [VALIDATION.md](VALIDATION.md) para verificações realizadas e pendências.
