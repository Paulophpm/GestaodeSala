Objetivo:

O Dashboard tem como objetivo de analisar os dados lançados pelos colaboradores que realizam a gestão de uma sala de um  estão localizados em 63 locais diferentes espalhados pelo Brasil ria e demostrar através de um dashboard a autonomia da gestão de sala de bateria de um determinado cliente.

Os dados são atualizados de forma periodica 

Dashboard:

![image](https://github.com/Paulophpm/GestaodeSala/assets/53667656/9fc3b0c5-6902-4bd1-8a80-1a1b3e9debd7)
 
Modelagem de Dados:
Fonte de Dados:
•	Formulário do Google Forms*;
•	Tabelas do Sharepoint**; (Inventário Maq) (Inventário Bat)
*gateway de dados;
**nível de conta organizacional;

##DP – Descarga Profunda:

Coluna Calculada que retorna caso a bateria tenha entrado em descarga profunda;


DP = SWITCH(
            TRUE,
            ISBLANK('Respostas ao formulário 1'[TENSÃO ]),
            'Respostas ao formulário 1'[Tensão Bat] = 48 && 'Respostas ao formulário 1'[TENSÃO ] < 47.7, 1,
            'Respostas ao formulário 1'[Tensão Bat] = 24 && 'Respostas ao formulário 1'[TENSÃO ] < 23.8, 1,
            'Respostas ao formulário 1'[Tensão Bat] = 80 && 'Respostas ao formulário 1'[TENSÃO ] < 72.3, 1,
            0)


Última Atualização:
Tabela inserida no Power Query para retornar a data e hora da última atualização da base de dados do dashboard;

Fonte = DateTimeZone.SwitchZone(DateTimeZone.LocalNow(),0,0)

Autonomia Bateria (h):

 
Tipo de Gráfico: Colunas Clusterizado;
•	Eixo X: ID da Máquina – Modelo (Concatenação);
•	Eixo Y: Média de Autonomia;
•	Linha Constante: Nível Crítico = 5 na Cor Vermelha com Rótulo dos Dados Ativado;
•	Linha Média: Cor = Azul
Visual:
•	Eixo X: Segoe UI tam 9;
•	Rótulo dos Dados: Tela de fundo – Transparência 60%;
•	Valores: Seguoe UI Tam 17 – Casas Decimais 1;
Geral:
•	Título: Cabeçalho 3 – DIN – 14 – Alinhado ao Centro – Quebra de Texto;
•	Efeitos:
•	Sombra: Deslocamento – Interno; Posição – Centralizar;

Autonomia de Máquina (h): 

 

Tipo de Gráfico: Colunas Clusterizado;
•	Eixo X: ID da Máquina – Modelo (Concatenação);
•	Eixo Y: Média de Autonomia;
•	Linha Constante: Nível Crítico = 5 na Cor Vermelha com Rótulo dos Dados Ativado;
•	Linha Média: 
Visual:
•	Eixo X: Segoe UI tam 9;
•	Rótulo dos Dados: Tela de fundo – Transparência 60%;
•	Valores: Seguoe UI Tam 17 – Casas Decimais 1;
Geral:
•	Título: Cabeçalho 3 – DIN – 14 – Alinhado ao Centro – Quebra de Texto;
•	Efeitos:
•	Sombra: Deslocamento – Interno; Posição – Centralizar;

Quantidade de Trocas Mês + DP:
 
Tipo de Gráfico: Colunas Clusterizado;
•	Eixo X: Mês do Ano;
•	Eixo Y: Média de Autonomia;
•	Eixo Y Secundário: DP – Porcentagem do total geral;
•	Linha Constante: Nível Crítico = 5 na Cor Vermelha com Rótulo dos Dados Ativado;
•	Linha Média: 
Visual:
•	Eixo X: Segoe UI tam 9;
•	Rótulo dos Dados: Tela de fundo – Transparência 60%;
•	Valores: Seguoe UI Tam 17 – Casas Decimais 1;
Geral:
•	Título: Cabeçalho 3 – DIN – 14 – Alinhado ao Centro – Quebra de Texto;
•	Efeitos:
•	Sombra: Deslocamento – Interno; Posição – Centralizar;
•	
Quantidade de Trocas Diárias:
 
Tipo de Gráfico: Colunas;
•	Eixo X: ID da Máquina – Modelo (Concatenação);
•	Eixo Y: Média de Autonomia;
•	Linha Constante: Nível Crítico = 5 na Cor Vermelha com Rótulo dos Dados Ativado;
•	Linha Média: 
Visual:
•	Eixo X: Segoe UI tam 9;
•	Rótulo dos Dados: Tela de fundo – Transparência 60%;
•	Valores: Seguoe UI Tam 17 – Casas Decimais 1;
Geral:
•	Título: Cabeçalho 3 – DIN – 14 – Alinhado ao Centro – Quebra de Texto;
•	Efeitos:
•	Sombra: Deslocamento – Interno; Posição – Centralizar;

Tabela de Trocas + Autonomia + DP:

 
Tipo de Gráfico: Colunas Clusterizado;
•	Eixo X: ID da Máquina – Modelo (Concatenação);
•	Eixo Y: Média de Autonomia;
•	Linha Constante: Nível Crítico = 5 na Cor Vermelha com Rótulo dos Dados Ativado;
•	Linha Média: 
Visual:
•	Eixo X: Segoe UI tam 9;
•	Rótulo dos Dados: Tela de fundo – Transparência 60%;
•	Valores: Seguoe UI Tam 17 – Casas Decimais 1;
Geral:
•	Título: Cabeçalho 3 – DIN – 14 – Alinhado ao Centro – Quebra de Texto;
•	Efeitos:
•	Sombra: Deslocamento – Interno; Posição – Centralizar;

Modelo Schema

•	Inventário de Bateria (1)  – > Respostas ao Formulário 1 (n) - Um para Muitos (1 - n)
•	Inventário Máq (n) < - > Inventário Bat (n) – Muitos para Muitos (n - n)


