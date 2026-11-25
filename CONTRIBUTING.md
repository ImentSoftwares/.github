# Guia de contribuição

Este guia vale para todos os repositórios da **ImentSoftwares** que não tenham um `CONTRIBUTING.md` próprio.

## Fluxo de trabalho (GitHub Flow)

1. A `main` é sempre estável e pronta para deploy. **Ninguém faz push direto nela.**
2. Crie uma branch a partir da `main` com um prefixo que indique o tipo:

   | Prefixo      | Uso                                   | Exemplo                       |
   |--------------|---------------------------------------|-------------------------------|
   | `feat/`      | nova funcionalidade                   | `feat/login-google`           |
   | `fix/`       | correção de bug                       | `fix/calculo-frete`           |
   | `hotfix/`    | correção urgente em produção          | `hotfix/erro-checkout`        |
   | `chore/`     | manutenção, deps, configs             | `chore/atualiza-node-22`      |
   | `docs/`      | documentação                          | `docs/readme-setup`           |
   | `refactor/`  | refatoração sem mudar comportamento   | `refactor/servico-pedidos`    |

3. Faça commits pequenos e frequentes.
4. Abra um Pull Request para a `main`, preencha o modelo e peça revisão.
5. Com o CI verde e a revisão aprovada, faça **Squash and merge** e apague a branch.

## Commits (Conventional Commits)

```
<tipo>(<escopo opcional>): <descrição no imperativo>
```

Tipos: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`.

Exemplos:

```
feat(auth): adiciona login com Google
fix(api): corrige timeout na listagem de pedidos
chore(deps): atualiza react para 19.1
```

Mudança que quebra compatibilidade: adicione `!` após o tipo (`feat!:`) e explique no rodapé com `BREAKING CHANGE:`.

## Pull Requests

- Um PR = um assunto. Prefira PRs pequenos (até ~400 linhas alteradas).
- O título do PR segue o padrão de commit, porque vira a mensagem do squash.
- Inclua prints ou vídeos para mudanças visuais.
- Pelo menos **1 aprovação** antes do merge.
- Resolva todas as conversas antes de mergear.

## Versionamento e releases

- Seguimos [SemVer](https://semver.org/lang/pt-BR/): `MAJOR.MINOR.PATCH`.
- Releases são criadas como tags `vX.Y.Z` com notas geradas a partir dos PRs.

## Padrões de repositório

Todo repositório novo deve ter:

- `README.md` com descrição, como rodar localmente e como fazer deploy
- `.gitignore` adequado à stack
- `.env.example` (nunca commitar `.env` ou segredos)
- `.editorconfig` e linter/formatter configurados
- CI rodando lint e testes em todo PR
- `CODEOWNERS` apontando para `@ImentSoftwares/core`

## Segredos

Nunca commite senhas, tokens ou chaves. Use **GitHub Secrets** (Actions) ou o gerenciador de segredos do provedor de deploy. Se um segredo vazar, revogue-o imediatamente. Apagar o commit não basta.
