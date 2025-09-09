# Flag Hunters (picoCTF)  
###### Solved by @RaquelTejo  

> Este é a resolução de um desafio de exploração em Python disponível na plataforma picoCTF.  

## Desafio: Flag Hunters  
#### Introdução  

O desafio **Flag Hunters** apresenta um programa em Python que simula a execução de letras musicais, com saltos entre versos e refrões, como se fossem chamadas de sub-rotinas.  
O detalhe importante é que existe uma parte escondida no início da música — onde está a flag — que o programa não imprime normalmente.  

- [Arquivo do código-fonte](https://challenge-files.picoctf.net/c_verbal_sleep/16af4dbf5dde07d6b920829561f50f7afe9e9e457733e422537c64525e1a6772/lyric-reader.py)
- Conexão remota com netcat:   

```bash 
nc verbal-sleep.picoctf.net 61366`
```

#### Análise e Exploração do desafio 

A vulnerabilidade do desafio está no modo como o programa manipula a entrada do usuário durante a execução da música.  
O objetivo é encontrar um meio de redirecionar o ponteiro de leitura (`lip`) para o início da letra, onde está escondida a flag.  

### 🔍 Entendendo o Código  

- O script carrega o conteúdo de `flag.txt` e armazena em `secret_intro`.  
- A função `reader()` começa a leitura a partir da label `[VERSE1]`, ignorando o trecho inicial que contém a flag.  
- Existe uma seção interativa **CROWD**, onde o programa solicita input do usuário.  
- Esse input substitui diretamente a linha atual da lista `song_lines`.  
  Isso significa que qualquer comando colocado aqui será posteriormente interpretado pelo programa.  

Trecho vulnerável:  

```python
elif re.match(r"CROWD.*", line):
    crowd = input('Crowd: ')
    song_lines[lip] = 'Crowd: ' + crowd 
    lip += 1
```
#### Resolução do desafio

Para resolver o desfio foi iniciada uma máquina virtual `Kali Linux`, onde foi aberto código no `Terminal`.
Através do input do `CROWD` escrevemos `;RETURN 0` para o programa reiniciar a leitura no `secret_intro` 

## Flag 

A flag é revelada no início da saída do script, através do arquivo lido flag.txt.

**Flag:** `picoCTF{70637h3r_f0r3v3r_a5202532}`
