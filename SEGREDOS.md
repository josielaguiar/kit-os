# Mapa de segredos — onde cada credencial vive

Este projeto pode acumular vários arquivos `.env` diferentes ao longo do tempo — isso é normal, não é bagunça: skills de API portáteis (que podem ser copiadas entre projetos) tendem a carregar a própria credencial junto, em vez de depender de um `.env` central. O importante não é ter só um lugar — é **nunca perder o rastro de onde cada um está** e confirmar que todos estão protegidos.

## Inventário

*(Preencher conforme os `.env` forem sendo criados — um por linha)*

| Arquivo | O que guarda | Protegido por |
|---|---|---|
| `.env` (raiz) | — | `.gitignore` raiz |

## Regra pra quando criar uma automação/skill nova

Se ela precisar de credencial própria:
1. Confirmar que existe um `.gitignore` cobrindo esse `.env` especificamente — não assumir que o `.gitignore` raiz já cobre. Testar com o comando abaixo.
2. Adicionar uma linha nova na tabela acima.

## Checklist de auditoria

Rodar da raiz do projeto sempre que desconfiar de algo, ou periodicamente:

```bash
# 1. Confirma que cada .env/segredo conhecido está de fato ignorado pelo git
git check-ignore -v "<caminho do arquivo>"
# (sem saída = NÃO protegido — alerta vermelho)

# 2. Acha qualquer .env ou arquivo de nome suspeito que apareceu desde a última auditoria
find . -name ".env" -not -path "*/node_modules/*" -not -path "*/.git*"
find . -iname "*token*" -o -iname "*secret*" -o -iname "*credencial*" -o -iname "*api*key*" | grep -v "node_modules\|/\.git"

# 3. Varre o CONTEÚDO de tudo que já está rastreado pelo git (não só nome de arquivo)
git grep -niE '(-----BEGIN [A-Z ]*PRIVATE KEY|ghp_[A-Za-z0-9]{30,}|AIza[A-Za-z0-9_-]{30,}|AKIA[A-Z0-9]{16}|sk-[A-Za-z0-9]{20,})'

# 4. Confirma que nenhuma pasta virou "sub-repositório" quebrado por engano
# (aconteceu numa limpeza real — arquivos reais somem, viram um ponteiro vazio)
git ls-files -s | awk '$1==160000'
# (qualquer linha aqui = problema — corrigir com: git rm --cached <caminho> && git add <caminho>)
```

Se as 4 checagens vierem limpas, os segredos estão seguros e a estrutura do repositório está íntegra.
