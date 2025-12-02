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
Nessa seção, ao abrir os **Index**, foi encontrado o comentário `No more information leaks!! Not even Google will find it this time...`, então abri manualmente o arquivo robots.txt adicionando `/robots.txt` ao final do link , ficando : `http://natas3.natas.labs.overthewire.org/robots.txt`. Dentro do robots.txt aparece: `Disallow: /s3cr3t/` , adicionando `/s3cr3t/` ao finaldo link fica: `http://natas3.natas.labs.overthewire.org/s3cr3t/` onde apresenta alguns arquivos, sendo um deles de texto, ao abri-lo conseguimos encontrar a senha para o level 4 `QryZXc2e0zahULdHrtHxzyYkj59kUxLQ`

## Flag

A flag obtida ao resolver o desafio é:

    QryZXc2e0zahULdHrtHxzyYkj59kUxLQ



## Level 4

- [Página do desafio](http://natas4.natas.labs.overthewire.org)  
> login : `natas4` senha : `QryZXc2e0zahULdHrtHxzyYkj59kUxLQ` 
#### Análise Inicial  

Ao acessar a página fornecida, mostra uma breve mensagem com uma dica.  
`Access disallowed. You are visiting from "" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"` e um botão de recarregar a página,clicando no botão a dica muda : `Access disallowed. You are visiting from "http://natas4.natas.labs.overthewire.org/index.php" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"`

Isso direciona a investigação não diretamente para dentro das informações do site.

#### Resolvendo o Level  

Para acessar a página corretamente, foi necessário enviar dois headers personalizados:

Authorization: o login do desafio (natas4 + senha) encodado em Base64

Referer: um valor falso apontando para:
http://natas5.natas.labs.overthewire.org/


Gerando o Authorization Base64

A credencial do nível é:
natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ


Esta string foi convertida para Base64 usando PowerShell:
$pair = "natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ"
$bytes = [System.Text.Encoding]::ASCII.GetBytes($pair)
$base64 = [Convert]::ToBase64String($bytes)


O resultado gerou o token usado em:
Authorization: Basic [base64]


Fazendo a requisição

Foi enviado:
Invoke-WebRequest `
  -Uri "http://natas4.natas.labs.overthewire.org/" `
  -Headers @{
    "Referer" = "http://natas5.natas.labs.overthewire.org/"
    "Authorization" = "Basic $base64"
  }
| Select-Object -ExpandProperty Content


O servidor aceita o Referer falso e responde com:

Access granted. The password for natas5 is `0n35PkggAPm2zbEpOU802c0x0Msn1ToK`


## Flag

A flag obtida ao resolver o desafio é:

    0n35PkggAPm2zbEpOU802c0x0Msn1ToK


## Level 5

- [Página do desafio](http://natas5.natas.labs.overthewire.org)  
> login : `natas5` senha : `0n35PkggAPm2zbEpOU802c0x0Msn1ToK` 
#### Análise Inicial  

Ao acessar a página fornecida, mostra uma breve mensagem com uma dica.  
`You are not logged in. `

Isso indica que o acesso depende de cookies, não de headers ou arquivos.

#### Resolvendo o Level  

Abrindo o DevTools (F12) na aba Application > Cookies, aparece: `loggedin = 0`,Mudando esse valor para: `loggedin = 1`  
e recarregar a página libera  a senha para o level 6 `0RoJwHdSKWFTYR5WuiAewauSuNaBXned`

## Flag

A flag obtida ao resolver o desafio é:

    0RoJwHdSKWFTYR5WuiAewauSuNaBXned


## Level 6

- [Página do desafio](http://natas6.natas.labs.overthewire.org)  
> login : `natas6` senha : `0RoJwHdSKWFTYR5WuiAewauSuNaBXned` 
#### Análise Inicial  

Ao acessar a página fornecida, exibe um formulário pedindo uma secret key.

#### Resolvendo o Level  

Ao abrir o código-fonte via View Source, encontra-se: `include "includes/secret.inc";`,Acessando manualmente: `http://natas6.natas.labs.overthewire.org/includes/secret.inc`  
dentro do arquivo encontramos a senha para o level 7 `bmg8SvU1LizuWjx3y7xkNERkHxGre0GS`

## Flag

A flag obtida ao resolver o desafio é:

    bmg8SvU1LizuWjx3y7xkNERkHxGre0GS


## Level 7

- [Página do desafio](http://natas7.natas.labs.overthewire.org)  
> login : `natas7` senha : `bmg8SvU1LizuWjx3y7xkNERkHxGre0GS` 
#### Análise Inicial  

Ao acessar a página fornecida, mostra uma breve mensagem com uma dica.  
`Try to look for the password in /etc/natas_webpass/natas8 `

#### Resolvendo o Level  

Na página montam URLs do tipo:`?page=about ?page=home`,Provavelmente vulnerável a Local File Inclusion (LFI). Basta fazer: `http://natas7.natas.labs.overthewire.org/?page=/etc/natas_webpass/natas8
` A senha para o level 8 aparece diretamente: `xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q`

## Flag

A flag obtida ao resolver o desafio é:

    xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q


## Level 8

- [Página do desafio](http://natas8.natas.labs.overthewire.org)  
> login : `natas8` senha : `xcoXLmzMkoIP9D7hlgPlh9XD7OgLAe5Q` 
#### Análise Inicial  

Ao acessar a página fornecida, mostra uma breve código:  
`$encodedSecret = base64_encode(strrev(bin2hex($secret))); `

#### Resolvendo o Level  

Reverter o processo:

Base64 decode

Reverter string

hex → texto

Inserir no formulário

A senha para o level 9 aparece diretamente: `ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t`

## Flag

A flag obtida ao resolver o desafio é:

    ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t

## Level 9

- [Página do desafio](http://natas9.natas.labs.overthewire.org)  
> login : `natas9` senha : `ZE1ck82lmdGIoErlhQgWND6j2Wzz6b6t` 
#### Análise Inicial  

Ao acessar a página fornecida, mostra uma breve mensagem com uma dica.  
`exec("grep -i $key dictionary.txt"); `

Ou seja, vulnerável a Command Injection.

#### Resolvendo o Level  

Inserir: `; cat /etc/natas_webpass/natas10`,O comando final executa:`grep -i '' dictionary.txt; cat /etc/natas_webpass/natas10]` conseguimos encontrar a senha para o level 10`t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu`

## Flag

A flag obtida ao resolver o desafio é:

    t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu



## Level 10

- [Página do desafio](http://natas10.natas.labs.overthewire.org)  
> login : `natas10` senha : `t7I5VHvpa14sJTUGV0cbEsbYfFP2dmOu` 
#### Análise Inicial  

Similar ao Level 9, mas agora tem um filtro: Só permite letras e espaço.

#### Resolvendo o Level  

O filtro não bloqueia: `.`E também aceita:`.*`Inserindo: `.* /etc/natas_webpass/natas11` Gera saída contendo a senha : ` UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk` 

## Flag

A flag obtida ao resolver o desafio é:

    UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk

## Level 11

- [Página do desafio](http://natas11.natas.labs.overthewire.org)  
> login : `natas11` senha : `UJdqkK1pTu6VLt9UHWAgRZz6sVUZ3lEk` 
#### Análise Inicial  

A página usa um cookie chamado data que é:

JSON

Criptografado com XOR

Codificado em base64

O código-fonte mostra a chave XOR.

#### Resolvendo o Level  

Decodificar o cookie

Fazer XOR reverso com a chave

Alterar "showpassword":"no" para "yes"

Re-XOR

Base64 encode

Inserir novo cookie no navegador 

A página revela a senha: yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB

## Flag

A flag obtida ao resolver o desafio é:

    yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB


## Level 12

- [Página do desafio](http://natas12.natas.labs.overthewire.org)  
> login : `natas12` senha : `yZdkjAYZRd3R7tq7T5kXMjMJlOIkzDeB` 
#### Análise Inicial  

Um formulário de upload de arquivo com extensão controlável.O código salva o arquivo mas não valida extensão real.

#### Resolvendo o Level  

OEnviar um arquivo .php com: `<?php echo file_get_contents("/etc/natas_webpass/natas13"); ?>`O site salva, basta acessar o arquivo no diretório indicado pela página e temos a senha : ` trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC` 

## Flag

A flag obtida ao resolver o desafio é:

    trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC


## Level 13

- [Página do desafio](http://natas13.natas.labs.overthewire.org)  
> login : `natas13` senha : `trbs5pCjCrkuSknBBKHhaBxq6Wm1j3LC` 
#### Análise Inicial  

Igual ao Level 12, mas agora verifica o magic number do arquivo.O site só aceita arquivos com assinatura de JPEG.

#### Resolvendo o Level  

Criar um arquivo com:

Início: bytes mágicos de JPEG

Depois: código PHP

Exemplo: `\xFF\xD8\xFF<?php echo file_get_contents("/etc/natas_webpass/natas14"); ?>`

Upload → abrir → senha aparece: ` z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ` 

## Flag

A flag obtida ao resolver o desafio é:

    z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ


## Level 14

- [Página do desafio](http://natas14.natas.labs.overthewire.org)  
> login : `natas14` senha : `z3UYcr4v4uBpeX8f7EZbMHlzK4UR2XtQ` 
#### Análise Inicial  

Formulário com login e senha.O código usa SQL sem proteção: `SELECT * FROM users WHERE username="$uname" AND password="$pass"` Vulnerável a SQL Injection.


#### Resolvendo o Level  

Inserir no usuário: `" OR "1"="1`Senha pode ser qualquer coisa. A consulta vira:`WHERE username="" OR "1"="1" `Entrando → mostra a senha : ` SdqIqBsFcz3yotlNYErZSZwblkm0lrvx` 

## Flag

A flag obtida ao resolver o desafio é:

    SdqIqBsFcz3yotlNYErZSZwblkm0lrvx



## Level 15

- [Página do desafio](http://natas15.natas.labs.overthewire.org)  
> login : `natas15` senha : `SdqIqBsFcz3yotlNYErZSZwblkm0lrvx` 
#### Análise Inicial  

Página com formulário de busca.
Código usa SQL, mas não retorna dados — apenas diz se existe ou não.
Isso força o uso de blind SQL injection.


#### Resolvendo o Level  

Usando uma payload do tipo: `natas16" AND password LIKE BINARY "a%" --`E variando caractere por caractere até formar a senha completa.

Automatizado (Python, bash, etc.), o script recupera toda a senha : ` hPkjKYviLQctEW33QmuXL6eDVfMW4sGo` 

## Flag

A flag obtida ao resolver o desafio é:

    hPkjKYviLQctEW33QmuXL6eDVfMW4sGo
