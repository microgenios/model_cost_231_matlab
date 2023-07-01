# model_cost_231_matlab
Modelo COST231 Walfish-Ikegami

% Modificado por Fernando Simplicio
% Ref: https://www.mathworks.com/matlabcentral/fileexchange/2224-cost231-models?focused=5045761&tab=function
% Tese: https://www.teses.usp.br/teses/disponiveis/3/3142/tde-07122006-170547/publico/FERRAMENTA_DE_SIMULACAO_COMPUTACIONAL_DE_CANAL_DE_PROPAGACAO.pdf
% FUNÇÃO PARA PREVISÃO DE PERDAS USANDO O MODELO "COST231-WI".
%
% Fonte bibliográfica: Principles and Applications of GSM
%                      Vijay K. Garg, Joseph E. Wilkes
%                      Prentice Hall,1999
%                      Páginas 270 e 273.
%
% saída = cost231wi(distancia, frequencia, hte, hre, ws, wb, hb, fi, los, zona)
%
% saída      : Vector com estimativas de predas, em função da distancia
%              para um valor fixo da frequencia
% distancia  : Vector com valores da distancia expressa em km,
% frequencia : Valor da frequência de trabalho, expressa em MHz,
% hte        : Altura da antena Emissora (em metros)
%	       Recomenda-se que esteja na gama [4,50] metros,
% hre        : Altura efectiva da antena no terminal movél (em metros)
%              Recomenda-se que esteja na gama [1,3] metros,
% ws	     : Largura da rua (expressa em metros), onde o terminal móvel
%	       se encontra; admite-se que este se localiza no centro da via,
% wb	     : Distancia média entre edificios, marcada entre os pontos
%	       centrais dos mesmos, para efeitos do calculo da média,
% hb	     : Altura média dos edificios; neste parametros, inclui-se a
%	       contribuição dos telhados,
% fi       : Orientação da via relativamente à união entre terminais (Graus);
% los      : condição de linha de vista
%            1- LOS
%            0 - NLOS;
% zona	  : Tipo de ambiente urbano em causa:
%	          1 - Grandes Centros Urbanos
%	          0 - Cidades de dimensões razoáveis ou areas Sub-urbanas.
%   

distancia = 576.03;         % m
frequencia = 918.0625000;   % MHz
hte = 7.3535;               % altura (m) da antena da base station (TX)
hre = 2;                    % altura (m) da antena do mobile (RX)
ws = 17.5;                  % largura da rua (m)
wb = 35;                    % distancia entre edificios (m)
hb = 4;                     % altura construção (m)
los = 0;                    % NLOS = 0
zona = 0;                   % 0 - Cidades de dimensões razoáveis ou areas Sub-urbanas.
fi = 90;                    % Orientação da via relativamente à união entre terminais (Graus);
perdas_db = -1* cost231wi(distancia/1000.0, frequencia, hte, hre, ws, wb, hb, fi, los, zona)
