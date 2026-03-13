RELATÓRIO TÉCNICO — ANÁLISE DE REDES SOCIAIS
Instagram e TikTok | Google Sheets
=============================================


1. CONTEXTO
-----------
Análise de dados de redes sociais de um cliente, com o objetivo de identificar
quais tipos de post performam melhor, em quais dias postar e como está o
crescimento de seguidores no Instagram e TikTok.

Dados fornecidos pelo cliente em formato Google Sheets com duas abas:
- Instagram: Data, Tipo de Post, Alcance, Impressões, Curtidas, Comentários,
  Compartilhamentos, Salvamentos, Seguidores no Dia
- TikTok: Data, Visualizações, Curtidas, Comentários, Compartilhamentos,
  Seguidores no Dia


2. LIMPEZA DE DADOS
-------------------
Antes de qualquer análise, os dados passaram pelo seguinte processo de limpeza:

- Datas padronizadas para o formato dd/mm/yyyy usando:
  =TEXTO(A2;"DD/MM/YYYY")

- Células vazias nas colunas Comentários, Compartilhamentos e Salvamentos
  foram mantidas em branco (não substituídas por 0), pois substituir por 0
  poderia distorcer cálculos de média — a origem dos valores vazios não foi
  confirmada pelo cliente.

- Números com formatação incorreta corrigidos (ex: 1.888 → 1888).

- Duplicatas removidas via: Dados > Limpeza de dados > Remover cópias.

- Verificação de consistência na coluna Tipo de Post (Instagram), garantindo
  que não havia variações como "Reels", "reel", "reels" misturadas.

- Verificação de valores negativos via filtro nas colunas numéricas de ambas
  as plataformas (Curtidas, Alcance, etc.).

- Datas inválidas ou fora do padrão corrigidas via filtro no TikTok.


3. ANÁLISE — INSTAGRAM
-----------------------

3.1 Tipo de Post
Tabela dinâmica criada com média de Alcance, Impressões, Curtidas, Comentários,
Compartilhamentos e Salvamentos por tipo de post.

Taxa de Engajamento calculada com a fórmula:
=(Curtidas + Comentários + Compartilhamentos + Salvamentos) / Alcance / 100

Resultados:
- Carrossel: engajamento 1,41%
- Foto:       engajamento 1,23%
- Reels:      engajamento 1,45% ← melhor formato
- Stories:    engajamento 1,11%

Reels também liderou em alcance médio (4.391) e curtidas (331).

3.2 Crescimento de Seguidores
Coluna "Ganho Diário de Seguidores" calculada com:
=SE(B3="";"";B3-B2)
(linha 2 sempre vazia pois não há dia anterior para comparar)

Gráfico de linha criado mostrando evolução de ~4.849 seguidores (jan/2025)
até ~5.560 (mar/2025) — crescimento consistente e saudável.

3.3 Dias da Semana
Coluna "Dia da Semana" extraída com: =TEXTO(A2;"dddd")

Tabela dinâmica com média de Alcance, Curtidas e Taxa de Engajamento por dia:

Dia            Alcance   Curtidas   Engajamento
-----------------------------------------------
Domingo        2.881     191        1,37%
Segunda-feira  1.956     142        1,28%
Terça-feira    2.148     142        1,39%  ← melhor engajamento
Quarta-feira   1.832     143        1,25%
Quinta-feira   2.158     174        1,38%
Sexta-feira    2.784     125        1,32%
Sábado         3.457     304        1,33%  ← maior alcance


4. ANÁLISE — TIKTOK
--------------------

4.1 Taxa de Engajamento
Calculada com:
=SE(C2="";"";(D2+E2+F2)/C2)
(sem dividir por 100, pois o Google Sheets já converte ao formatar como %)

No TikTok o engajamento é calculado sobre Visualizações (não Alcance),
por isso os percentuais são naturalmente menores.

4.2 Dias da Semana
Tabela dinâmica com média de Visualizações, Curtidas, Comentários,
Compartilhamentos e Engajamento por dia:

Dia            Visualizações   Engajamento
------------------------------------------
Domingo        13.637          11,61%  ← melhor engajamento
Segunda-feira  9.810           8,70%
Terça-feira    12.933          10,39%
Quarta-feira   34.192          10,38%  ← maior alcance (disparado)
Quinta-feira   21.437          9,28%
Sexta-feira    10.803          10,09%
Sábado         14.956          9,07%

4.3 Crescimento de Seguidores
Coluna "Ganho Diário de Seguidores" calculada com:
=SE(G3="";"";G3-G2)
(seguidores na coluna G; linha 2 sempre vazia)

Gráfico de linha criado mostrando evolução de seguidores ao longo do período.


5. DASHBOARD
------------
Página Dashboard criada com:
- Cards de insights visuais (Instagram e TikTok lado a lado)
- Gráfico de linha: Crescimento de Seguidores — Instagram
- Gráfico de linha: Crescimento de Seguidores — TikTok
- Gráfico de barras: Dias da semana x Alcance — Instagram
- Gráfico de barras: Dias da semana x Visualizações — TikTok
- Gráfico de barras: Tipo de post x Alcance — Instagram


6. RECOMENDAÇÕES FINAIS
-----------------------
Instagram:
- Priorizar Reels (melhor alcance e engajamento)
- Postar no sábado para maximizar alcance
- Postar na terça-feira para maximizar engajamento
- Estratégia ideal: Reels na terça ou sábado

TikTok:
- Postar na quarta-feira para maximizar visualizações
- Postar no domingo para maximizar engajamento
- A conta apresenta crescimento sólido de seguidores no período analisado
