# artigo-fontes-dados-goias
Repositório de dados e códigos do artigo acadêmico que investiga as fontes de dados no jornalismo goiano, utilizando análise de conteúdo e classificação automatizada com inteligência artificial.

# De onde vêm os dados? Mapeamento das fontes de informação no jornalismo goiano

Scripts e dados do artigo acadêmico que investiga as fontes de dados utilizadas por veículos jornalísticos goianos na produção de reportagens.

## Sobre a pesquisa

Este estudo analisou **600 matérias** de três veículos de comunicação de Goiás:
- **G1 Goiás** (200 matérias)
- **Jornal Opção** (200 matérias)
- **Lab Notícias** (200 matérias)

O objetivo foi mapear quais instituições, órgãos e entidades fornecem os dados quantitativos que fundamentam a produção jornalística local.

### Principais achados

- **44,3%** das matérias utilizam dados quantitativos
- **IBGE** é a principal fonte (6,5% das menções)
- **Órgãos federais** concentram 22,4% das fontes citadas
- Forte dependência de fontes federais, com subutilização de fontes locais como o **IMB** (Instituto Mauro Borges)

## Metodologia

A classificação das matérias seguiu o **nível 5 da matriz de Mancini e Vasconcellos (2016)**, que identifica matérias que utilizam dados de forma ilustrativa.

Para a análise automatizada, foi desenvolvido um script em Python utilizando:
- **pydantic-ai** para estruturação de dados
- **Google Gemini (gemini-2.5-flash-lite)** como modelo de linguagem

O sistema extrai três elementos de cada matéria:
1. Instituição fonte do dado
2. Indicador social mencionado
3. Valor citado

## Estrutura do repositório

```
├── README.md
├── dados/
│   ├── g1_noticias.csv                    # Matérias brutas do G1 Goiás
│   ├── jornal_opcao_noticias.csv          # Matérias brutas do Jornal Opção
│   ├── lab_noticias.csv                   # Matérias brutas do Lab Notícias
│   └── classificados/
│       ├── g1_noticias_mancini.csv        # G1 com classificação Mancini
│       ├── jornal_opcao_noticias_mancini.csv
│       └── lab_noticias_mancini.csv
├── scripts/
│   └── classificacao_mancini.ipynb        # Notebook de classificação com IA
└── artigo/
    └── artigo_fontes_dados_goias.pdf      # Artigo completo
```

## Como usar

### Pré-requisitos

```bash
pip install pydantic-ai google-genai pandas nest_asyncio
```

### Configuração

1. Obtenha uma API key do Google AI Studio
2. Configure a variável de ambiente ou use o Google Colab com `userdata`

### Executando a classificação

```python
import os
os.environ["GOOGLE_API_KEY"] = "sua-api-key"

# Execute o notebook classificacao_mancini.ipynb
```

## Resultados

| Veículo | Total | Com dados | % |
|---------|-------|-----------|---|
| G1 Goiás | 200 | 30 | 15% |
| Jornal Opção | 200 | 106 | 53% |
| Lab Notícias | 200 | 130 | 65% |
| **Total** | **600** | **266** | **44,3%** |

### Top 5 fontes mais citadas

1. IBGE (39 menções)
2. Ministério da Saúde (21 menções)
3. Cimehgo (14 menções)
4. OMS (12 menções)
5. TSE (11 menções)

## Referencial teórico

- MANCINI, L.; VASCONCELLOS, F. **Jornalismo de Dados: conceito e categorias**. Fronteiras - estudos midiáticos, v. 18, n. 1, p. 69-82, 2016.
- BARDIN, L. **Análise de Conteúdo**. São Paulo: Edições 70, 2011.
- TRÄSEL, M. **Jornalismo guiado por dados: aproximações entre a identidade jornalística e a cultura hacker**. Estudos em Jornalismo e Mídia, v. 11, n. 1, p. 291-304, 2014.
- PERUZZO, C. M. K. **Mídia regional e local: aspectos conceituais e tendências**. Comunicação & Sociedade, n. 43, p. 67-84, 2005.

## Autoria

**Sofia Souza Costa**  
Graduanda em Jornalismo - Universidade Federal de Goiás (UFG)

## 📄 Licença

Este projeto está sob a licença MIT. Os dados coletados são de fontes públicas e foram utilizados para fins acadêmicos.

## 🔗 Citação

Se utilizar este trabalho, por favor cite:

```
COSTA, Sofia Souza. De onde vêm os dados? Mapeamento das fontes de informação 
no jornalismo goiano. 2025. Artigo (Graduação em Jornalismo) - Faculdade de 
Informação e Comunicação, Universidade Federal de Goiás, Goiânia, 2025.
```

---

*Trabalho desenvolvido como parte da disciplina de Iniciação Científica do curso de Jornalismo da Universidade Federal de Goiás em dezembro de 2025.*
