# Testando login por certificado

Agora é a hora de testarmos o login via certificado! Para testar basta acessar novamente o ssh da mesma maneira:

```
tvs@tablucas:~$ ssh root@10.10.5.2
Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-43-generic x86_64)

root@root-server:~# 
```

Desta vez, a única senha que ele irá pedir é a do certificado, não a do servidor. A segurança maior está no fato de que a senha nunca vai para o servidor. Ao invés disso, as informações são criptografadas diretamente com o o certificado.