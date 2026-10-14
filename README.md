# dio
Repositório para entregas de desafios dos cursos DIO

Objetivo do desafio era criar uma planilha com cara de aplicativo para responder cinco perguntas:

1. Quanto investir por mês;
2. Por quantos anos;
3. Qual a taxa de rendimento mensal;
4. Quanto de patrimônio vai acumular;
5. Quanto vai receber de dividendos por mês.

Além disso, também deveria projetar o patrimônio em cenários de 2 a 30 anos e dar sugestões de como dividir aporte entre os seis tipos de FIIs, conforme perfil de investidor escolhido.


As perguntas de 1 a 3 são campos que o investidor deve preencher de acordo com suas capacidades e objetivos

Já a pergunta 4 é um campo que utiliza a fórmula VF (FV em inglês) para calcular o patrimônio acumulado com base nos valores preenchidos pelo usuário nos campos que respondem as perguntas de 1 a 3. 

Por fim, pergunta 5 também é respondida pelo cálculo de multiplicação entre patrimônio acumulado e rendimento da carteira

Há ainda um campo de sugestão de investimento com base no salário do investidor.

<img width="572" height="426" alt="image" src="https://github.com/user-attachments/assets/843ee285-7de1-4d62-ba85-a4b0adb62bc7" />

Para facilitar o acompanhamento e checagem das fórmulas foram criadas os seguintes intervalos nomeados: 

D15 = salario
D16 = rendimento_carteira
D17 = sugestao_investimento
D20 = aporte_mensal
D21 = qtd_anos
D22 = taxa_mensal
D23 = patrimonio
D24 = dividendos
C34 = perfil

Alguns exemplos de campos preenchidos utilizando intervalos nomeados são:

Patrimônio Acumulado: =FV(taxa_mensal;qtd_anos*12;aporte_mensal*-1)
Dividendos Mensais: =patrimonio*rendimento_carteira
Projeção cenários: =FV(taxa_mensal;$A30*12;investimento_mensal*-1)
Percentual sugerido: =VLOOKUP(CONCAT(Perfil;"-";B38);'tabela apoio'!$A$2:$D$20;4;0)

Fórmula PROCV (VLOOKUP) foi utilizada para atualizar campos de percentuais sugeridos por perfil de investidor de forma dinâmica. Para isso foi necessário criar identificadores chave único para cada perfil e tipo de FII e uma aba nova com a tabela de apoio com os percentuais referentes a cada um desses identificadores.

Principal mudança em relação à ferramenta do Expert foi adicionar um SE (IF) na fórmula de preenchimento de valores sugeridos para cada tipo de FII, dessa forma a tabela retorna um "-" e não "R$ 0,00" nos casos que o percentual sugerido era 0%, tornando tabela visualmente mais agradável.

Valores sugeridos para cada tipo de FII: =IF(aporte_mensal*C40=0;"-";aporte_mensal*C40)

<img width="560" height="244" alt="image" src="https://github.com/user-attachments/assets/6a918925-c5a4-4382-90a3-89fbc968aca1" />





