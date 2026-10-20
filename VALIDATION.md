# Validação do tutorial

Data: 2026-10-20.

## Escopo e fontes

O tutorial vive neste repositório independente. A preparação deve gerar somente
o guia e o ignore locais, inicializar Git quando apropriado e instalar as skills.
O exercício é produzido nos chats posteriores, com aprovação da especificação.

O único ambiente do roteiro é **VS Code no Windows com a extensão Codex
executando no WSL2**. Git, Python 3, a pasta do exercício e as seis skills
pertencem à mesma distribuição e ao usuário Linux dessa execução. O destino
de instalação é `$HOME/.agents/skills` na home Linux efetiva. Todos os prompts,
o guia gerado e as verificações de descoberta seguem esse contexto.

Os contratos das seis skills e os metadados `agents/openai.yaml` foram lidos na
fonte local e comparados com a revisão pública
`075ea3ffb228e596bdb3b2b3ca769aad858b31cd` de
[codex-skills](https://github.com/renanfranca/codex-skills/tree/075ea3ffb228e596bdb3b2b3ca769aad858b31cd).
A revisão inclui as referências obrigatórias de `refactor-design`.

## Compatibilidade dos prompts

| Skill | O que o roteiro exige |
| --- | --- |
| `specify-issue` | Pesquisa inicial somente de leitura; proposta em Plan; aprovação explícita em outro turno; gravação apenas da especificação em inglês; sem Git ou implementação nessa etapa. |
| `implement-execplan` | Plano completo entre chats, gravado antes do código, mantido em marcos e na entrega. Deve conservar as cinco seções obrigatórias e os contratos dos marcos definidos pela skill. |
| `plan-behavioral-acceptance` | Fontes, exemplos, verificações e evidências por requisito; expectativa e suficiência da prova avaliadas separadamente; planejamento sem implementação. |
| `tdd-behavior-autonomous-quiet` | Um comportamento por ciclo, suíte relevante red antes da produção e green depois; testes pela CLI; evidências registradas nos marcos, sem exigir narração de cada ciclo. |
| `refactor-design` | Comportamento completo, suíte e caminho público verdes antes da revisão; leitura da rubrica obrigatória; preservação do contrato; No action justificado permitido. |
| `commit-the-changes` | Status, histórico e diff antes de stage; seleção apenas do trabalho autorizado; sem histórico, convenção explicitamente indicada; hash e assunto na entrega. |

## Verificações locais realizadas

- Markdown: `npx --yes markdownlint-cli2@0.23.3 README.md VALIDATION.md`,
  código 0, nenhum problema. A configuração permite `details`/`summary` e
  linhas longas em prompts e tabelas, mantendo as demais regras padrão.
- Links locais: verificador
  [check_markdown_links.py](https://github.com/renanfranca/codex-skills/blob/075ea3ffb228e596bdb3b2b3ca769aad858b31cd/restructure-documentation/scripts/check_markdown_links.py)
  da fonte, recebendo `README.md` e `VALIDATION.md`, código 0.
- Links externos de referência: consultados sem autenticação, todos com
  HTTP 200, incluindo as orientações oficiais de WSL2 e da configuração
  `chatgpt.runCodexInWindowsSubsystemForLinux` da extensão.
- Consistência do roteiro: oito etapas preservadas, todos os prompts situam a
  execução no WSL2 e as instruções de preparação usam ferramentas Linux,
  `python3 -X utf8` e a home Linux para instalar as seis skills. O guia local
  recebe distribuição, caminhos e comandos desse ambiente.
- Comandos Linux: `git --version`, `python3 --version`, resolução dos dois
  executáveis e importação de `unittest`/`venv` conferidas num shell cujo kernel
  identifica WSL2. Isso não demonstra execução pela extensão.
- Whitespace e quebra de linha final conferidos. A meta de cinco minutos
  permanece pendente de cronometragem na extensão; contagem de palavras não
  substitui essa verificação.
- Distribuição das skills: clone temporário da revisão pública, comparação
  SHA-256 dos **14 arquivos** das seis pastas com a fonte local e com cópias em
  destino temporário; todos idênticos. Inclui metadados e ambas as referências
  de revisão estrutural. Reutilização de destinos idênticos conferida sem
  escrita. Isso valida a cópia, não a descoberta nem a ativação na extensão.

## Publicação conferida

- Repositório `renanfranca/codex-workflow-tutorial` público, branch principal
  `main`, confirmados por GitHub CLI e requisição anônima à API do GitHub.
- Página inicial acessível sem autenticação com HTTP 200 e título do README
  presente; README bruto em `main` com HTTP 200 e conteúdo idêntico ao local.
- Commit inicial `f137c7d`, `docs: add Codex workflow tutorial`, confirmado no
  remoto `refs/heads/main`. Árvore local limpa após o envio inicial.
- `git diff --cached --check` passou antes do commit. Nenhuma alteração ou
  publicação foi feita no repositório de skills ou no de memória.

## Verificações ainda pendentes na extensão

Na inspeção inicial não foi encontrado pacote da extensão Codex nos inventários
locais consultados do VS Code Windows e do servidor WSL2. Não houve execução
interativa na extensão com o roteiro atualizado para WSL2.
Assim, permanecem **não verificados**:

- Receber somente a URL e executar a preparação, incluindo a recuperação
  “Siga este tutorial”.
- Conexão do VS Code e execução dos comandos da extensão na distribuição WSL2
  selecionada, incluindo a recuperação quando o processo estiver fora dela.
- Instalação das seis skills na home Linux dessa distribuição, descoberta no
  seletor/contexto e ativação observada durante os respectivos chats.
- Rerun da preparação reconhecendo exercício existente sem sobrescrever nada;
  tratamento interativo de ferramentas ausentes e autoria não configurada.
- Resultado de execução dos prompts, incluindo evidências red/green reais,
  duas saudações pela CLI, revisão estrutural e commit do exercício.
- Cronometragem da leitura e ações do participante; a meta de cinco minutos
  não é um resultado medido.

Para concluir essa validação, abra uma pasta vazia na home Linux pela conexão
WSL2 do VS Code Windows e use a extensão Codex autenticada nessa distribuição.
Comprove o ambiente dos comandos do Codex e execute o README. Cronometre leitura,
cópias e ações de interface, pausando durante esperas do Codex, downloads e
preparação de ferramentas ausentes. Registre distribuição, home Linux efetiva,
caminhos de Git/Python/skills, versão da extensão, modelos/esforços disponíveis
e tempos ativo/excluído separadamente. Inspecione os arquivos depois da
preparação, repita a entrada para conferir preservação e complete o ciclo.
Confira em `EXECPLAN.md` as provas de cada requisito e, com o Git Linux, o hash
e o conteúdo do commit. Registre falhas sem convertê-las em sucesso.
