# Ataque a Máquina 

Para analisar a vulnerabilidade de uma máquina, utilizei o `Nmap` para verificar as portas abertas e os serviços em execução.

Comando Nmap:

```
map 192.168.10.41 -p- -sV 
```
![image](https://github.com/Dianilze/Dianilze/assets/133764203/38afab03-3856-4471-82b2-d92c917e5664)

E o NMAP identificou várias portas abertas e os serviços associados.

Resultado do Nmap:

* Porta 22/tcp: Aberta, serviço SSH (OpenSSH 9.2p1 Debian 2+deb12u1).
* Porta 80/tcp: Aberta, serviço HTTP (Apache httpd 2.4.57 Debian).
* Porta 443/tcp: Aberta, serviço HTTPS (Greenbone Security Assistant).
* Porta 3000/tcp: Aberta, serviço não reconhecido.
* Porta 8000/tcp: Aberta, serviço HTTP (Apache httpd 2.4.57 Debian).


Como todas as máquinas que o professor nos deu tem como o user o `wargame` então tornou mais facil.

Como a porta 22/tcp estava aberta com o serviço SSH em execução, decidi realizar um ataque de força bruta com o Hydra, considerando que todas as máquinas fornecidas pelo professor usam o usuário "wargame".

Criei uma lista `pass.txt` com os possíveis combinações.

Comando Hydra:

shell
```
hydra -l wargame -P /home/sarah/Downloads/pass.txt ssh://192.1168.10.41
```

![image](https://github.com/Dianilze/Dianilze/assets/133764203/a4d260f3-3336-4fb9-b1e1-6f9ab29998af)

O resultado foi `ctfwar23`.

Então executei ssh e consegui entrar na maquína.



  


- 👋 Hi, I’m @Dianilze
