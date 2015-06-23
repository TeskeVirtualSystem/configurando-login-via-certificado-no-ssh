# Verificando a existência de uma chave RSA local

# Criando a chave RSA local

O primeiro passo para a autenticação via certificado é criar uma chave SSH local. Para isso, deve-se executar o seguinte comando em uma janela terminal:

    ssh-keygen -t rsa
    

Ele irá perguntar algumas coisas. A primeira delas é o caminho a onde a chave deve ser salva. Deixe o caminho padrão apertando apenas a tecla **ENTER**. Após isso, será pedido uma senha para seu certificado. Essa senha será usada para descriptografar o seu certificado toda vez que for usá-lo. 

Vale lembrar que a maioria das distribuições linux tem o hábito de salvar a senha na sessão. Isso faz desnecessário que se digite a senha repetidamente todas as vezes que for usar o certificado.

Use uma senha segura para proteger seu certificado.

```
tvs@tablucas:~$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/tvs/.ssh/id_rsa): 
Created directory '/home/tvs/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/tvs/.ssh/id_rsa.
Your public key has been saved in /home/tvs/.ssh/id_rsa.pub.
The key fingerprint is:
e1:70:7f:a6:57:c9:58:bf:e6:be:87:59:1d:a3:ee:06 tvs@tablucas
The key's randomart image is:
+---[RSA 2048]----+
|                 |
|                 |
|                 |
|         +    . .|
|        S . . .Eo|
|       . + + ..*.|
|          + o oo=|
|             o.==|
|              +oo|
+-----------------+

```

Feito isso, seu certificado está criado!