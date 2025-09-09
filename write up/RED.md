# RED (picoCTF)  
###### Solved by @RaquelTejo
> Este é a resolução de um desafio desafio de forense RED da plataforma picoCTF. A resolução envolve analisar pistas, inspecionar metadados e extrair informações ocultas em uma imagem utilizando esteganografia LSB (Least Significant Bit).
## Desafio: RED
#### Introdução  

O desafio fornece uma imagem chamada red.png, que, como o nome sugere, parece ser apenas uma imagem completamente vermelha. O objetivo é descobrir a flag escondida dentro do arquivo.

As dicas fornecidas pelo enunciado são:

`"The picture seems pure, but is it though?"`

`"Red?Ged?Bed?Aed?"`

`"Check whatever Facebook is called now."`
 

#### Solução 

A resolução começa pela interpretação das dicas:

###### 1. Análise das pistas

A primeira impressão da imagem é que ela é apenas vermelha.

As menções a “Red, Ged, Bed, Aed” nos remetem aos canais de cor: Vermelho (Red), Verde (Green), Azul (Blue) e Alfa (Alpha).

A presença do canal Alpha sugere que devemos analisar a imagem no formato RGBA.

Isso indica o uso de esteganografia LSB, uma técnica que esconde dados nos bits menos significativos de cada canal de cor.


###### 2. Escolha da ferramenta

Para manipulação e extração dos dados, utilizamos o [CyberChef](https://gchq.github.io/CyberChef)

O CyberChef permite processar a imagem diretamente no navegador, extraindo os bits LSB e decodificando o conteúdo oculto de forma prática.
#### Execução com CyberChef
A solução no CyberChef seguiu dois passos principais:

###### 1. Extrair LSB

Carregamos o arquivo red.png no campo Input.

Adicionamos a operação Extract LSB na receita.

Configuramos a extração para Red, Green, Blue e Alpha, mantendo a ordem RGBA.

A saída resultante foi uma longa string de texto, que aparentava ser Base64.


###### 2. Decodificar Base64

Adicionamos a operação From Base64 logo após a extração LSB.

O CyberChef utilizou a saída da etapa anterior como entrada.

O resultado final revelou a flag legível.
## Flag

A flag obtida ao resolver o desafio é:

    picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}



