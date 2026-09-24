# Kit-base — Claude Code OS

Kit-base pessoal pra iniciar um novo workspace de negócio com o Claude Code. Baseado no mecanismo do curso Claude Code OS (Ratos de IA), com ajustes feitos depois de rodar uma versão real (Sixcont) por meses: sem hook de auto-sync silencioso, `.gitignore` já testado, e `SEGREDOS.md` como parte do padrão desde o início.

## Como usar pra começar um projeto novo

1. Clonar este repositório numa pasta nova com o nome do negócio/projeto
2. Abrir o Claude Code nessa pasta
3. Rodar `/setup` — entrevista curta sobre quem você é, o que faz e como trabalha
4. Rodar `/mapear` — mapeia seus processos do dia a dia e cria skills personalizadas
5. Rodar `/syncar` quando quiser conectar num repositório do GitHub próprio desse projeto novo (não deste kit)

## O que tem aqui

- `.claude/commands/setup.md` — entrevista de configuração inicial
- `.claude/commands/mapear.md` — mapeamento de processos e criação de skills
- `.claude/commands/iniciar.md` — carrega contexto no início de cada sessão
- `.claude/commands/syncar.md` — salva o projeto no GitHub (manual, explícito, nunca mexe em `.env`)
- `templates/perfis/` — estruturas de pasta por tipo de negócio (agência, empresa, freelancer, solopreneur)
- `templates/skills/` — skills prontas pra adaptar (carrossel, proposta comercial, roteiro de post, etc.)
- `templates/ferramentas/catalogo.md` — MCPs e ferramentas conhecidas, cruzadas durante o `/mapear`
- `_contexto/`, `marca/design-guide.md` — placeholders vazios, preenchidos pelo `/setup`
- `SEGREDOS.md` — convenção e checklist de auditoria de credenciais, pra manter desde o primeiro dia

## Não tem aqui (de propósito)

Nenhum conteúdo de negócio real — nenhum cliente, nenhuma automação, nenhuma credencial. Isso é só o mecanismo; o conteúdo nasce em cada projeto que usar este kit.
