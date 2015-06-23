# Configurando o servidor SSH para a autenticação

O próximo passo é configurar a máquina alvo para que aceite a autenticação via 
chave RSA. Para isso é necessário ter sua `chave pública` em algum lugar fácil para se copiar. Sua `chave pública` está armazenada em `~/.ssh/id_rsa.pub`.

```
tvs@tablucas:~$ cat ~/.ssh/id_rsa.pub 
ssh-rsa AAAAB3NBBBC1yc2EAAAADAQABAAABAQDFH/Z3Lh3a67/XgRedfysEDC1G3Qn/ttZZRq1dp0bXSKyTehpQHGymk5a2+F6F5LzEYL0AAAi2aFl56bqTDo6/VRgkOvXw6EWgJAkIGm0Prh2uSH5cobFSHdA9L4J7U62pLfzZINuBEkgCBrFo+zAvXF8e7BBOdWc/NSAAABRT/A3NLmAAAIv7PPREFETCHgeQbqforbTKOAZ8mEUtctS2HFVLMZuXDhuVJT72YcR2h9faVTkFHERY7RajwBl6eFA7N/sxMjqt+R2qcZZZZZZtOSuxuUvbn/nOwR8LLO0sngefIzQhpwtmUOfEs94060ognPe05s/HUEBRBR tvs@tablucas
```

Neste caso, a `chave pública` é : 

```
ssh-rsa AAAAB3NBBBC1yc2EAAAADAQABAAABAQDFH/Z3Lh3a67/XgRedfysEDC1G3Qn/ttZZRq1dp0bXSKyTehpQHGymk5a2+F6F5LzEYL0AAAi2aFl56bqTDo6/VRgkOvXw6EWgJAkIGm0Prh2uSH5cobFSHdA9L4J7U62pLfzZINuBEkgCBrFo+zAvXF8e7BBOdWc/NSAAABRT/A3NLmAAAIv7PPREFETCHgeQbqforbTKOAZ8mEUtctS2HFVLMZuXDhuVJT72YcR2h9faVTkFHERY7RajwBl6eFA7N/sxMjqt+R2qcZZZZZZtOSuxuUvbn/nOwR8LLO0sngefIzQhpwtmUOfEs94060ognPe05s/HUEBRBR tvs@tablucas
```

# Acessando servidor e configurando chave pública


Agora precisamos acessar o servidor alvo usando uma autenticaçao de senha normal.
Para isso, basta acessarmos via ssh normal:

```
tvs@tablucas:~$ ssh root@10.10.5.2
The authenticity of host '10.10.5.2 (10.10.5.2)' can't be established.
ECDSA key fingerprint is XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.10.5.2' (ECDSA) to the list of known hosts.
root@10.10.5.2's password: 
Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-43-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

533 packages can be updated.
277 updates are security updates.

*** /dev/sda1 will be checked for errors at next reboot ***
*** /dev/sda5 should be checked for errors ***
*** /dev/sdd1 should be checked for errors ***

Last login: Wed May 27 10:35:50 2015 from nblucas.local

```