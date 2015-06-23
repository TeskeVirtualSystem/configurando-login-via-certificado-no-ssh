# Observações

## O certificado é vinculado aos usuários

A chave `RSA` local foi criada para o usuário que você estava autenticado. Por 
esse motivo, apenas ele irá usar essa chave quando for se conectar a um servidor
ssh. Por outro lado, a chave pública foi inserida **apenas** para o usuário ao
qual você logou no servidor. Sendo assim, você irá apenas acessar aquele usuário
sem uma senha. Para acessar outros usuários, o procedimento de adição da `chave
pública` ao servidor será repetido para todos os usuários desejados


## Problema de permissão no `authorized_keys`

Em alguns casos o servidor SSH pode reclamar as permissões no arquivo `~/.ssh/authorized_keys` e simplesmente ignorar o login via chave. Para resolver
isso basta acertar as permissões para **644** do arquivo:

    chmod 644 ~/.ssh/authorized_keys
    
