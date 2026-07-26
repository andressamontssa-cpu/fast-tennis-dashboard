# Dashboard Fast Tennis — publicação no GitHub Pages

Este pacote tem tudo que é preciso para publicar o dashboard num link único, que
qualquer pessoa autorizada pode acessar de qualquer computador — sem precisar
reenviar o arquivo por e-mail ou WhatsApp a cada atualização.

## O que tem aqui

- `index.html` — o dashboard completo (v122), já com:
  - uma **tela de senha na abertura**, bloqueando a visualização de qualquer
    dado até digitar a senha;
  - busca automática de **unidades novas** a partir de uma Planilha Google e
    (como reforço) do arquivo `dados_atualizacao.json`.
- `dados_atualizacao.json` — fonte alternativa/manual para unidades novas
  (explicado mais abaixo). A fonte principal agora é a Planilha Google.

## Sobre os dados sensíveis — decisão já aplicada

O dashboard tem faturamento, lucro líquido, breakeven e outros dados
financeiros por unidade. O GitHub Pages **gratuito só publica em repositórios
públicos** — qualquer pessoa com o link (inclusive buscadores) chegaria à
página. Para não depender de um plano pago do GitHub, adicionei uma **tela de
senha na abertura do próprio dashboard**: ninguém vê nenhum dado sem digitar a
senha primeiro, mesmo com o repositório público.

- Senha de **visualização** (tela de entrada, para quem só vai olhar o
  dashboard): `ft2026`
- Senha de **upload/cadastro** (para carregar planilhas ou cadastrar unidade
  nova): `9083` — a mesma de sempre, sem mudança.

São senhas propositalmente separadas, para você poder compartilhar a de
visualização com franqueados/gestores sem dar acesso de alterar dados. **Não é
uma segurança de nível bancário** — quem souber abrir o código-fonte da página
consegue ver a senha — mas evita que alguém esbarre no link por acaso e veja
os números sem querer.

Para trocar a senha de visualização, procure por `VIEW_PASSWORD` dentro do
`index.html` (uma única linha) e troque o valor entre aspas. Se preferir, me
peça para eu trocar e gerar uma nova versão.

Há um botão **"🔒 Bloquear"** na barra superior do dashboard, para forçar a
tela de senha de novo (útil se o dashboard for aberto num computador
compartilhado).

## Passo a passo para publicar

1. Crie uma conta no GitHub (github.com), se ainda não tiver.
2. Crie um repositório novo (ex.: `fast-tennis-dashboard`). Pode ficar
   público — a tela de senha já protege o acesso casual.
3. Envie os dois arquivos deste pacote (`index.html` e
   `dados_atualizacao.json`) para dentro do repositório (dá pra arrastar e
   soltar direto pela própria página do GitHub, em "Add file → Upload
   files").
4. Vá em **Settings → Pages** do repositório, escolha a branch `main` e a
   pasta raiz (`/`), e salve.
5. Em alguns minutos o GitHub mostra o link público, algo como:
   `https://seuusuario.github.io/fast-tennis-dashboard/`
6. Esse é o link único que todo mundo usa a partir de agora (pedindo a senha
   `ft2026` na entrada).

## Planilha Google — Metas do Mês / Faturamento (piloto)

Criei também a planilha **"Fast Tennis - Metas do Mês (Faturamento)"**, já
preenchida com todo o histórico de Janeiro a Julho/2026 que hoje está
embutido no dashboard (nada foi perdido). Colunas: Mês (AAAA-MM), Unidade,
Gerente, Fat. Meta, Tendência, Real D-1, Inadimplência, Ticket Médio, Base
Clientes, Meta de Vendas, Vendas Realizadas.

A partir de agora, em vez de gerar e subir a planilha oficial pelo botão "💰
Metas do Mês", basta **atualizar essa planilha** (repita cada unidade todo
mês com os números novos — sem apagar os meses anteriores, que continuam
valendo como histórico). O dashboard busca sozinho e os dados da planilha
**têm prioridade** sobre o que está embutido no arquivo para aquele mês e
unidade — ou seja, uma correção feita na planilha sempre vale.

Mesma pendência da planilha de unidades novas: abra esta planilha → botão
Compartilhar → mude o acesso geral para **"Qualquer pessoa com o link" →
Leitor**.

Este é um piloto: se funcionar bem para você, o mesmo modelo dá para estender
para Custo Fixo/Lucro Líquido e Leads/Conversão (estruturas parecidas, uma
linha por unidade por mês) e, por último, para a Base de Clientes completa
(mais complexa — ~34 mil linhas, com cálculo de churn e ocupação — por isso
prefiro deixá-la para depois de validar o piloto).

## Planilha Google — cadastro de unidades novas (fonte principal)

Criei uma Planilha Google na sua conta chamada **"Fast Tennis - Cadastro de
Novas Unidades"**, já com as colunas certas: Nome da Unidade, Estado (UF),
Cidade, Gerente, Quadras Adulto, Quadras Infantil, Nome na planilha de Vendas
(opcional), Data de Cadastro.

O dashboard busca essa planilha sozinho toda vez que alguém abre a página. Ou
seja: a partir de agora, para cadastrar uma unidade nova valendo para todo
mundo, basta **adicionar uma linha nessa planilha** — não precisa mais editar
nada no GitHub.

**Passo que só falta você fazer** (não consigo fazer por você): abra a
planilha no Google Drive → botão **Compartilhar** → em "Acesso geral", mude
de "Restrito" para **"Qualquer pessoa com o link"**, com papel **Leitor**.
Sem isso, o dashboard não consegue ler a planilha (ela continua privada por
padrão). Ninguém consegue editar com esse acesso — só ler.

Se, depois disso, o dashboard ainda não conseguir buscar a planilha (alguns
navegadores bloqueiam esse tipo de busca por segurança — CORS), me avise que
eu troco para o link de "Publicar na web" (Arquivo → Compartilhar → Publicar
na Web → formato CSV), que é o formato oficial do Google para esse uso e
sempre funciona.

O botão "➕ Nova Unidade" do próprio dashboard continua funcionando do mesmo
jeito de antes (cadastro imediato só naquele navegador + download de um JSON
de apoio) — a diferença é que agora, para valer para todo mundo, o caminho
recomendado é colar a mesma informação na planilha, em vez de editar o
`dados_atualizacao.json` no GitHub. Ainda dá pra usar o `dados_atualizacao.json`
como alternativa manual se preferir.

## Como funcionam as atualizações depois de publicado

- **Dados gerais (faturamento, vendas, metas, custo fixo, quadras etc.):**
  continuam sendo atualizados do mesmo jeito de sempre — você me envia os
  dados, eu gero uma nova versão do `index.html`, e você substitui esse
  arquivo no repositório (mesmo processo do passo 3, mas sobrescrevendo o
  arquivo existente). Assim que subir, o link já mostra a versão nova para
  todo mundo.

- **Unidades novas:** adicione uma linha na Planilha Google (fonte principal,
  ver acima). Em poucos minutos, todo mundo que abrir o link já vê a unidade
  nova, sem precisar mexer em nada no GitHub.
