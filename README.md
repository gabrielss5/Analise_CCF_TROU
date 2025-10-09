⚙️ Classificador de TROU — CCF Analyzer

Este aplicativo utiliza o output do CCF (Combinações de Condições Faltantes ou Duplicadas) e a tabela mestre de versões para identificar automaticamente se cada TROU (falta) é verdadeiro ou falso.

O app foi desenvolvido para automatizar a análise mensal de inconsistências no PLM, reduzindo o tempo de verificação manual e eliminando falsos positivos.

🧠 O que o aplicativo faz

Lê o arquivo CCF com as combinações de atributos.

Lê a tabela mestre de versões contendo todas as versões e seus atributos válidos.

Compara as combinações do CCF com as combinações reais existentes.

Classifica automaticamente:

✅ TROU verdadeiro → combinação realmente faltante.

⚠️ TROU falso → combinação inexistente no projeto (falso positivo).

Gera um arquivo Excel final com os resultados classificados e as versões impactadas.


📄 Arquivos de entrada

📘 1. Arquivo CCF

Exportado do PLM (geralmente .xlsx), deve conter:

| DECOUPAGE PSA NP | Désignation NP    | Etat PA | Cas d´emploi épuré/Combinaison manquante |
| ---------------- | ----------------- | ------- | ---------------------------------------- |
| R1B01001         | PARE-CHOCS AR ASS | TROU    | [DDJ:04].[DEE:31].[DEW:07].[DQK:00]...   |


📗 2. Tabela Mestre de Versões

Arquivo .xlsx com as colunas:

| Version           | Pack | Attribut |
| ----------------- | ---- | -------- |
| 1PPA5D415GLA00C04 | A    | DDJ04    |
| 1PPA5D415GLA00C04 | A    | DEE31    |

Essa tabela deve conter todas as versões válidas e seus atributos associados, incluindo os atributos de base (B0D, B0E, etc).

📤 Saída

O aplicativo gera um arquivo Excel com a classificação automática das combinações.
Exemplo:

| DECOUPAGE | NP    | Estado | Combinação           | Classificação   | Versão Impactada  |
| --------- | ----- | ------ | -------------------- | --------------- | ----------------- |
| Y4A01001  | NP001 | TROU   | [DDJ:04].[DEE:31]... | TROU Falso      | —                 |
| Y4A01002  | NP002 | TROU   | [DDJ:04].[DEE:00]... | TROU Verdadeiro | 1PPA5D415GLA00C04 |


👤 Créditos

Desenvolvido por Gabriel Silveira Silva
Cargo: RCD
💡 Projeto criado para otimizar e automatizar processos de análise de TROUS apontados no CCF e ICONE do projeto.
