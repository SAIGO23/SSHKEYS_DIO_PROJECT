# SSHKEYS_DIO_PROJECT
Open-Source project_SSHKEYS_DIO_PROJECT
# SSHKEYS_DIO_PROJECT

## Descrição
O **SSHKEYS_DIO_PROJECT** é um CLI simples para auxiliar equipes na geração e gestão de chaves SSH, garantindo segurança no ciclo de desenvolvimento de software. O projeto facilita a criação, armazenamento e uso correto de chaves SSH, evitando problemas de autenticação e configurando-as corretamente para repositórios remotos como GitHub e GitLab.

---

## Instalação

Para usar o projeto, basta clonar o repositório e garantir que você tem o **OpenSSH** instalado em seu sistema:

```bash
# Clone este repositório
git clone https://github.com/seu-usuario/SSHKEYS_DIO_PROJECT.git
cd SSHKEYS_DIO_PROJECT
```

Se estiver usando Windows, instale o OpenSSH via **Git Bash** ou **WSL**.

---

## Como Usar

### 1. Gerar uma nova chave SSH

Execute o seguinte comando:

```bash
ssh-keygen -t ed25519 -C "seu_email@exemplo.com"
```

Se preferir RSA:

```bash
ssh-keygen -t rsa -b 4096 -C "seu_email@exemplo.com"
```

Pressione **Enter** para aceitar o local padrão (`~/.ssh/id_ed25519` ou `id_rsa`).

### 2. Adicionar a chave ao agente SSH

Para garantir que a chave seja carregada corretamente:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

Caso esteja usando RSA:

```bash
ssh-add ~/.ssh/id_rsa
```

### 3. Copiar a chave pública

```bash
cat ~/.ssh/id_ed25519.pub
```

Ou, se for RSA:

```bash
cat ~/.ssh/id_rsa.pub
```

Copie o texto gerado e adicione no seu provedor de código (GitHub/GitLab).

### 4. Testar a conexão

Para testar se a chave está funcionando:

```bash
ssh -T git@github.com
```

Se aparecer:

```
Hi [SeuUsuário]! You've successfully authenticated, but GitHub does not provide shell access.
```

Significa que a configuração foi bem-sucedida. 🎉

---

## Configuração opcional: Multiplicar chaves SSH
Se você gerencia diferentes chaves SSH para GitHub e GitLab, pode configurar o arquivo `~/.ssh/config`:

```bash
nano ~/.ssh/config
```

E adicione:

```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519
  IdentitiesOnly yes

Host gitlab.com
  HostName gitlab.com
  User git
  IdentityFile ~/.ssh/id_ed25519_gitlab
  IdentitiesOnly yes
```

Isso ajuda o SSH a escolher a chave correta automaticamente.

---

## Contribuição
Contribuições são bem-vindas! Se quiser sugerir melhorias ou relatar bugs, abra uma **Issue** ou envie um **Pull Request**.

1. Faça um fork do repositório
2. Crie um branch para a sua feature (`git checkout -b minha-feature`)
3. Faça commit das mudanças (`git commit -m 'Adiciona nova feature'`)
4. Faça push para o branch (`git push origin minha-feature`)
5. Abra um Pull Request

---

## Licença
Este projeto está sob a licença MIT. Veja o arquivo **LICENSE** para mais detalhes.

---

**Feito com ❤️ para a comunidade open-source!** 🚀

