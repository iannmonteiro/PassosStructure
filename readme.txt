# Preparando arquivo input #
1) Abrir o editor de texto e inserir informações do arquivo.nex 
Arquivo: (=) Pra separar os genes

# Fist gene: coi
>AmostraA
ACCTTTGGGCCTA
>AmostraB
TACCCTTGGCCTA
=
# Second gene: nd2
>AmostraA
CCATTTGGGCCTA
>AmostraB
GGGCCTTGGCCTA
=

# Salvar o arquivo .txt #
2) Colar o arquivo na pasta do xmfa2struct

# Pra rodar o xmfa2struct
3) Como o arquivo é em C, usar o "./" antes do nome do programa:
  ./xmfa2struct.win inputfile.txt output.txt

# Verificar se todos os blocos foram lidos e verificar comprimento total #
____________________________________________________________________________
# Rodando STRUCTURE #
1) File > New Project

2) Nome do projeto; Localização da pasta; Arquivo de entrada (gerado no xmfa2)

3) Setar informações do arquivo de entrada:
  Número de indivíduos:
  Ploidia dos dados: 2 ou 1
  Números de loci: Olhar quantas colunas, exceto pelo nome da amostra
  Missing data: -9

4) Selecionar "Map distance between loci"
5) Selecionar "Individual ID for each individual" 

6) Parameter Set > New
  Burnin: 100.000
  MCMC: 900.000

  Ancestry Model > Use Admixture Model
  Allele Frequency Model > Allele Frequency Correlated
  Advancced > Compute Probability 
            > Print Credible regiions

7) Project > Start a job
  K: Valor que vc quer testar +2
  Number of Interations: 5 a 10

START
___________________________________________________________
# Analisando Resultados #

1) Entrar no arquivo de corrida do Structure e zipar a pasta resultados (que contem várias corridas de K)

2) Copiar pasta para pasta do "structureHarvester-master" (Download aqui: https://github.com/dentearl/structureHarvester/blob/master/README.md)

3) Abrir prompt e usar "structureHarvester.py --dir=Clicar_e_arrastar_a_pasta_pra_ca --out=escolhernomedapastaout"
    Irá gerar um summary com as corridas

4)"structureHarvester.py --dir=Nomedoarquivo.rar --out=escolhernomedapastaout --clumpp"
    Utilizar para gerar os arquivos indfile, que serão utilizados no Clumpp

5) Copia o arquivo com o .indfile com o K a ser usado e cola dentro da pasta do clumpp

6) Abre o arquivo paramfile (que vem com o programa Clumpp) e altera:
  6.1) Onde está escrito "arabid.formato" alterar para o nome do arquivo de K.formato
  6.2) Troque o primeiro Datatype igual a 0
  6.3) Altere o melhor K, N de individuos e nº de runs. Salva e clica no Clumpp que irá rodar automaticamente.

7) Use os resultados output no excel.

