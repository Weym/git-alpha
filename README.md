# Configurando GitHub SSH

## Passo 1: Gerar uma nova chave

```bash
ssh-keygen -t ed25519 -C "email@exemplo.com"
```

Depois vai ser perguntado sobre uma frase secreta, uma medida adicional de segurança

## Passo 2: Iniciar o SSH Agent e adicionar a chave

SSH agente gerencia as chaves em memória
```bash
eval "$(ssh-agent -s)"
```

Adicionar a chave criada ao agente:
```bash
ssh-add ~/.ssh/id_ed25519
```
Se criou uma frase secreta, vai ser pedido para repetir

## Passo 3: Copiar a chave pública

Mostrar a chave pública para que possa copiar e adicionar ao Github

```bash
cat ~/.ssh/id_ed25519.pub
```

A chave pública vai ser algo parecido com:

```
ssh-ed25519 AAAAC3NzaC1... email@exemplo.com
```

Copie tudo desde o ssh até o final, incluindo o email

## Passo 4: Adicionar a chave ao GitHub

Siga os passos:

1. Ir até [SSH e GPG Keys](https://github.com/settings/keys) no GitHub
2. Clicar em "Nova Chave SSH"
3. Preencher o formulário
4. Adicionar a chave

## Passo 5: Testar a conexão SSH
Verificar se funciona corretamente
```bash
ssh -T git@github.com
```

Na primeira conexão, vai receber um aviso sobre a autenticidade do host, digite `yes` e dê enter

Vai receber uma mensagem parecida com:
> Hi username! You've successfully authenticated, but GitHub does not provide shell access.

## Passo 6: Configurar o Git (se necessário)

```bash
git config --global user.name "Seu nome"
git config --global user.email "seuemail@exemplo.com"
```