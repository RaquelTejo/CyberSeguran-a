# Natas Level 0 ao Level 15
###### Solved by @RaquelTejo
> Este é a resolução do desafio 0 ao 15 da plataforma [Natas](https://overthewire.org/wargames/natas/).  

#### Introdução  

Os desafios do Natas faz parte da categoria *web-security* .  
A proposta é analisar o funcionamento de uma aplicação web simples e o objetivo final é descobrir a flag oculta, que é a senha para acessar o próximo level  

## Level 0

- [Página do desafio](http://natas0.natas.labs.overthewire.org)  
> login : `natas0` senha : `natas0` 
#### Análise Inicial  

Ao acessar a página fornecida, mostra uma breve mensagem com uma dica.  
`You can find the password for the next level on this page.`

Isso direciona a investigação diretamente para dentro das informações do site.  

#### Resolvendo o Level  

Apertando o botão direito do mouse em qualquer lugar do site e clicando em `inspecionar elemento`, foi possível acessar a aba `Sources`  
Nessa seção, ao abrir os **Index**, foi encontrado a senha para o level 1 `0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq`.  

## Flag

A flag obtida ao resolver o desafio é:

    0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq


## Level 1

- [Página do desafio](http://natas1.natas.labs.overthewire.org)  
> login : `natas1` senha : `0nzCigAq7t2iALyvU9xcHlYN4MlkIwlq` 
#### Análise Inicial  

Ao acessar a página fornecida, mostra uma breve mensagem com uma dica.  
`You can find the password for the next level on this page, but rightclicking has been blocked!`

Isso direciona a investigação diretamente para dentro das informações do site. Mas dessa vez não podemos usar o botão direito do mouse.  

#### Resolvendo o Level  

Apertando `CTRL + SHIFT + C`, foi possível acessar a aba `Sources`  
Nessa seção, ao abrir os **Index**, foi encontrado a senha para o level 2 `TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI`.  

## Flag

A flag obtida ao resolver o desafio é:

    TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI



## Level 2

- [Página do desafio](http://natas2.natas.labs.overthewire.org)  
> login : `natas2` senha : `TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI` 
#### Análise Inicial  

Ao acessar a página fornecida, mostra uma breve mensagem com uma dica.  
`There is nothing on this page `

Isso direciona a investigação não diretamente para dentro das informações do site.

#### Resolvendo o Level  

Apertando `CTRL + SHIFT + C`, foi possível acessar a aba `Elements`  
Nessa seção, ao abrir os **body**, foi encontrado um link de png  `http://natas2.natas.labs.overthewire.org/files/pixel.png`.
Ao apagar a parte `pixel.png` fica : `http://natas2.natas.labs.overthewire.org/files/` onde apresenta alguns arquivos, sendo um deles de texto, ao abri-lo conseguimops encontrar a senha para o level 3 `3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH`

## Flag

A flag obtida ao resolver o desafio é:

    3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH

## Level 3

- [Página do desafio]( http://natas3.natas.labs.overthewire.org)  
> login : `natas3` senha : `3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH` 
#### Análise Inicial  

Ao acessar a página fornecida, mostra uma breve mensagem com uma dica.  
`There is nothing on this page `

Isso direciona a investigação não diretamente para dentro das informações do site.

#### Resolvendo o Level  

Apertando `CTRL + SHIFT + C`, foi possível acessar a aba `Sources`  
Nessa seção, ao abrir os **Index**, foi encontrado o comentário `No more information leaks!! Not even Google will find it this time...`, então abri manualmente o arquivo robots.txt adicionando `/robots.txt` ao final do link , ficando : `http://natas3.natas.labs.overthewire.org/robots.txt`. Dentro do robots.txt aparece: `Disallow: /s3cr3t/` , adicionando `/s3cr3t/` ao finaldo link fica: `http://natas3.natas.labs.overthewire.org/s3cr3t/` onde apresenta alguns arquivos, sendo um deles de texto, ao abri-lo conseguimops encontrar a senha para o level 4 `QryZXc2e0zahULdHrtHxzyYkj59kUxLQ`

## Flag

A flag obtida ao resolver o desafio é:

    QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
