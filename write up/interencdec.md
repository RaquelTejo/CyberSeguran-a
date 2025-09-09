# interencdec (picoCTF)  
###### Solved by @RaquelTejo
> Este é a resolução de um desafio de decodificação da plataforma picoCTF.  

## Desafio: interencdec
#### Introdução  

O desafio consiste em um único arquivo [enc_flag](https://artifacts.picoctf.net/c_titan/108/enc_flag), acompanhado do enunciado:

"Can you get the real meaning from this file?"

O objetivo é descobrir o conteúdo original escondido nesse arquivo. 

 

#### Solução 

A resolução foi conduzida em etapas, cada uma lidando com uma camada específica de criptografia ou codificação.

###### 1. Primeira Camada: Base64

O arquivo enc_flag foi aberto no editor Visual Studio Code, revelando o seguinte conteúdo: `YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyZzBOMm8yYXpZNWZRPT0nCg==`

A presença de letras maiúsculas e minúsculas, números e o sufixo `==` indicam fortemente que se trata de uma codificação Base64.
Para decodificação, utilizamos o site: [dcodebase64](https://www.dcode.fr/code-base-64)
###### 2. Segunda Camada: Base64 Aninhado

Decodificando a primeira string, obtemos outra sequência de bytes que ainda aparenta estar codificada em Base64:
`b'dM0JqdkpBTXhqaGx6aHlfazNqelT3YTNRclX2g0N2o2azY5fQ=='`

Ou seja, o arquivo continha Base64 dentro de Base64. Ao extrair e decodificar esta segunda camada, chegamos a:
`s0IqdjITXhqhlzh_k3jzS7a3QCrW2g4N7j6kY9}`

###### 3. Decifragem Final: Cifra de César

A string restante estava protegida por uma Cifra de César, exigindo aplicar uma rotação correta nos caracteres para recuperar a mensagem original.

Após aplicar a rotação adequada, a string é finalmente decodificada, revelando a flag completa.

## Flag

A flag obtida ao resolver o desafio é:

    picoCTF{caesar_d3cr9pt3d_a47c6d69}



