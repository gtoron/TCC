# 🦴 OSSOS_NOVO

Estimativa de **estatura** de populações pretéritas do **Pantanal brasileiro** a partir do **comprimento de ossos longos** (fêmur, tíbia, úmero, rádio e ulna).

## Conteúdo

```
.
├── OSSOS_NOVO.rda     # dados, funções, tabelas, teste estatístico e gráficos (R)
├── DOCUMENTACAO.md    # documentação detalhada (variáveis, equações, objetos)
└── README.md
```

## Dados

- **35 indivíduos** de 3 sítios (`MT-PO-44`, `MS-CP-61`, `MT-PO-38`), curados na `UFMS/LAPan`, `UERJ/LAB` e `IHB`.
- Medidas ósseas em **mm** (lados esquerdo `.e` e direito `.d`); estaturas estimadas em **cm** (colunas `esta.*`).
- Sexo codificado como `1` (masculino), `2` (feminino) e `3` (indeterminado).
- Valores ausentes (`NA`) indicam osso não preservado.

## Como usar

```r
load("OSSOS_NOVO.rda")

# Estatura a partir de um fêmur de 378 mm, homem adulto
est.femur(femur = 378, est.sexo = "1", est.idade = "Adulto")   # ≈ 147,8 cm

# Estatura média por sexo
aggregate(esta.media ~ est.sexo, data = tabela.final, FUN = mean)
```

## Método

Equações de regressão específicas por sexo, na forma:

```
Estatura (cm) = (a + b × x/10) × 0.996 + 11.7      (x = comprimento em mm)
```

- Apenas indivíduos **adultos** recebem estimativa.
- Sexo indeterminado: média das equações masculina e feminina.
- `esta.media` é a média das estimativas disponíveis de cada indivíduo.

Fonte das equações: *[inserir referência]*

## Resultado resumido

Estatura média da amostra: **159,4 cm** (DP = 7,2; 145,4 a 178,1 cm). Teste de Wilcoxon entre sexos: W = 70, p = 0,131.

## Cuidados

Amostra pequena e com ossos preservados de forma desigual; equações podem não refletir a população estudada. Os remanescentes humanos devem ser tratados conforme a legislação e as normas das instituições de guarda.

## Requisitos

R e `ggplot2` (gráficos salvos com a versão 3.5.1).

## Citação e licença

*[Como citar]* · *[Licença]* · *[Contato]*
