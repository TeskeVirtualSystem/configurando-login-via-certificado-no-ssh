# Verificando a existência de uma chave RSA local

Antes de prosseguir, é necessário verificar se já não foi gerada uma chave RSA 
local. Caso já exista, não será necessário re-criar uma chave para os acessos e 
o passo seguinte poderá ser pulado.

Para verificar a existência de uma chave já criada em seu usuário, verifique a 
existência do arquivo `~/.ssh/id_rsa.pub` da seguinte maneira:

    cat ~/.ssh/id_rsa.pub
    
Se você tiver uma chave pública como o resultado abaixo, você já tem uma chave
criada.

```
tvs@tablucas:~$ cat ~/.ssh/id_rsa.pub 
ssh-rsa AAAAB3NBBBC1yc2EAAAADAQABAAABAQDFH/Z3Lh3a67/XgRedfysEDC1G3Qn/ttZZRq1dp0bXSKyTehpQHGymk5a2+F6F5LzEYL0AAAi2a
Fl56bqTDo6/VRgkOvXw6EWgJAkIGm0Prh2uSH5cobFSHdA9L4J7U62pLfzZINuBEkgCBrFo+zAvXF8e7BBOdWc/NSAAABRT/A3NLmAAAIv7PPREFET
CHgeQbqforbTKOAZ8mEUtctS2HFVLMZuXDhuVJT72YcR2h9faVTkFHERY7RajwBl6eFA7N/sxMjqt+R2qcZZZZZZtOSuxuUvbn/nOwR8LLO0sngefI
zQhpwtmUOfEs94060ognPe05s/HUEBRBR tvs@tablucas
```

