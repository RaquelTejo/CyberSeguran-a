# Cookie Monster Secret Recipe (picoCTF)  
###### Solved by @RaquelTejo
> Este é a resolução de um desafio de cyber segurança da plataforma [picoCTF](https://picoctf.org/).  

## Desafio: Cookie Monster Secret Recipe (Web Exploitation)  
#### Introdução  

O desafio **Cookie Monster Secret Recipe** faz parte da categoria *Web Exploitation* do [picoCTF](https://picoctf.org/).  
A proposta é analisar o funcionamento de uma aplicação web simples que utiliza cookies para armazenar informações do usuário.  
O objetivo final é descobrir a flag oculta nos cookies do site manipulando esses dados.  

- [Página do desafio](http://verbal-sleep.picoctf.net:58340)  

#### Análise Inicial  

Ao acessar o endereço fornecido, a página mostra uma breve mensagem com uma dica.  
Essa indicação sugere que a identidade do usuário não é armazenada em banco de dados ou sessão de servidor, mas sim em cookies.  

Isso direciona a investigação diretamente para os cookies do site.  

#### Inspeção dos Cookies  

Utilizando as ferramentas de desenvolvedor do navegador (`Ctrl + Shift + i`), foi possível acessar a aba **Application** (ou **Storage**, dependendo do navegador).  
Nessa seção, ao abrir os **Cookies**, foi encontrado um registro chamado `name`.  

O valor armazenado nesse cookie era uma sequência em formato base64:  `cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzXzQ3MzZGNkNCfQ%3D%3D`

#### Decodificação 

Para descodificar o valor achado nos Cookies, foi utilizado o site [dcode](https://www.dcode.fr/code-base-64).

## Flag

A flag obtida ao resolver o desafio é:

    picoCTF{c00k1e_m0nster_l0ves_c00kies_4736F6CB}

