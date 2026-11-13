[README.md](https://github.com/user-attachments/files/34810878/README.md)
# Site da Ana Júlia: publicar no GitHub Pages com domínio próprio

Este repositório tem só o `index.html`, que já vem criptografado. Os textos (bilhetes, frases e missões) só aparecem com a senha, então não tem problema o repositório ser público.

## 1. Criar o repositório

1. Entre em https://github.com/new
2. Dê um nome discreto ao repositório, por exemplo `nosso-cantinho`.
3. Deixe como **Public**. O GitHub Pages grátis exige repositório público.
4. Clique em **Create repository**.
5. Na tela seguinte, clique em **uploading an existing file**.
6. Arraste o `index.html` e clique em **Commit changes**.

## 2. Ligar o GitHub Pages

1. No repositório, vá em **Settings → Pages**.
2. Em **Source**, escolha **Deploy from a branch**.
3. Em **Branch**, escolha `main`, pasta `/ (root)`, e clique em **Save**.
4. Em 1 a 2 minutos o site fica no ar em:
   `https://matheus1906-hash.github.io/nosso-cantinho/`

## 3. Configurar o domínio próprio

Neste exemplo o domínio é `seudominio.com`. Troque pelo que você comprou.

### No painel do registrador (Cloudflare ou Porkbun), seção DNS

Apague os registros A/AAAA/CNAME padrão que já existirem para `@` e `www`. Depois crie estes:

| Tipo  | Nome | Valor                        |
|-------|------|------------------------------|
| A     | @    | 185.199.108.153              |
| A     | @    | 185.199.109.153              |
| A     | @    | 185.199.110.153              |
| A     | @    | 185.199.111.153              |
| AAAA  | @    | 2606:50c0:8000::153          |
| AAAA  | @    | 2606:50c0:8001::153          |
| AAAA  | @    | 2606:50c0:8002::153          |
| AAAA  | @    | 2606:50c0:8003::153          |
| CNAME | www  | matheus1906-hash.github.io   |

**Se for Cloudflare:** deixe a nuvem de proxy **cinza (DNS only)** em todos esses registros, pelo menos até o HTTPS do GitHub ficar ativo.

### No GitHub

1. **Settings → Pages → Custom domain**: digite `seudominio.com` e clique em **Save**. O GitHub cria sozinho um arquivo `CNAME` no repositório.
2. Espere a verificação de DNS ficar verde. Pode levar de alguns minutos até algumas horas.
3. Marque **Enforce HTTPS**. Se a opção estiver desabilitada, espere até 1 hora e recarregue a página.

O HTTPS é **obrigatório**: sem ele o navegador não libera a criptografia e a senha não funciona.

### Recomendado: verificar o domínio

Vá em **Settings (da sua conta) → Pages → Add a domain** e siga as instruções. Você vai criar um registro TXT no DNS. Isso impede que outra pessoa use o seu domínio no GitHub Pages.

## Atualizar o site depois

Para trocar o site, suba um novo `index.html` no repositório: **Add file → Upload files**, substituindo o antigo. Em 1 a 2 minutos a nova versão fica no ar.
