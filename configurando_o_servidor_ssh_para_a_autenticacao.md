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

root@root-server:~# 
```

Feito isso, teremos que adicionar a chave publica  ao arquivo `~/.ssh/authorized_keys`:

    echo "ssh-rsa AAAAB3NBBBC1yc2EAAAADAQABAAABAQDFH/Z3Lh3a67/XgRedfysEDC1G3Qn/ttZZRq1dp0bXSKyTehpQHGymk5a2+F6F5LzEYL0AAAi2aFl56bqTDo6/VRgkOvXw6EWgJAkIGm0Prh2uSH5cobFSHdA9L4J7U62pLfzZINuBEkgCBrFo+zAvXF8e7BBOdWc/NSAAABRT/A3NLmAAAIv7PPREFETCHgeQbqforbTKOAZ8mEUtctS2HFVLMZuXDhuVJT72YcR2h9faVTkFHERY7RajwBl6eFA7N/sxMjqt+R2qcZZZZZZtOSuxuUvbn/nOwR8LLO0sngefIzQhpwtmUOfEs94060ognPe05s/HUEBRBR tvs@tablucas" >> ~/.ssh/authorized_keys
    
Ou editando o arquivo e adicionando a linha. Dependendo de como você copiou, pode ser que a sentença esteja com quebras de linha. Todo trecho desde **ssh-rsa** até **usuario@maquina** deverá estar em apenas uma linha. No arquivo `authorized_keys` será uma chave por linha.

# Testando login por certificado

Agora é a hora de testarmos o login via certificado! Para testar basta acessar novamente o ssh da mesma maneira:

```
tvs@tablucas:~$ ssh root@10.10.5.2
Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-43-generic x86_64)

root@root-server:~# 
```

Desta vez, a única senha que ele irá pedir é a do certificado, não a do servidor. A segurança maior está no fato de que a senha nunca vai para o servidor. Ao invés disso, as informações são criptografadas diretamente com o o certificado.