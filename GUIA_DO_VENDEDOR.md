# Guia do vendedor (uso interno, não vai para o cliente)

Esta pasta é separada do produto. Aqui fica o que é seu: página de vendas, link de pagamento e o processo de entrega. O produto (`prumo-crm`) é entregue limpo, sem nada daqui.

## Modelo de entrega

O cliente recebe tudo e fica dono de tudo:

1. **Planilha pronta** (link `/copy`): ao abrir, ele faz uma cópia na conta Google dele, com o script dentro.
2. **Pacote limpo** (`prumo-crm-v1.0.0.zip`): pasta `site` para subir no GitHub dele, `planilha/Codigo.gs` (caso precise colar o script de novo) e os guias.
3. **Vídeos**: montar o script na planilha, publicar o Apps Script e subir o site no GitHub Pages. O roteiro dos vídeos segue o `docs/INSTALACAO.md` do pacote.

Nenhum servidor seu fica no caminho. Se você parar de vender amanhã, o cliente continua usando.

## Gerar o pacote limpo

Na pasta do produto:

```bash
node ferramentas/empacotar.js
```

Gera `prumo-crm/dist/prumo-crm-v1.0.0.zip` sem histórico do git, sem testes e sem informações suas.

## Criar a planilha-modelo (uma vez por versão)

1. Crie uma planilha em branco na sua conta Google, com um nome neutro, por exemplo "Prumo CRM".
2. Extensões > Apps Script > cole o `planilha/Codigo.gs` do pacote > salve. **Não rode o instalar** (quem instala é o cliente, com o e-mail dele).
3. Compartilhar > Qualquer pessoa com o link > Leitor.
4. Troque o final do link de `/edit...` por `/copy`:
   `https://docs.google.com/spreadsheets/d/ID_DA_PLANILHA/copy`

Atenção: a cópia mostra ao cliente quem é o dono da planilha original (o seu nome de conta Google). Se não quiser isso, crie a planilha-modelo numa conta Google só do produto.

## Página de vendas

`index.html` desta pasta. Antes de publicar, preencha no fim do arquivo:

- `LINK_PAGAMENTO`: link de pagamento do Mercado Pago (Seu negócio > Link de pagamento)
- `PRECO`: valor exibido
- `LINK_DEMO`: endereço de uma instalação sua do sistema com `?demo=1` no fim (a demonstração roda só no navegador, não precisa de servidor)

Ela pode ir para um repositório próprio no GitHub Pages ou entrar como página da Brasa.

## Sugestão de ofertas

| Oferta | O que inclui |
|---|---|
| Licença | Planilha, pacote, guias e vídeos. Pagamento único. |
| Licença + instalação | Você instala por chamada e deixa funil e automações configurados. |
| Servidor de WhatsApp gerenciado (opcional) | Você hospeda a Evolution API para o cliente. Único item mensal, opcional. |

## Termos para deixar claros na venda

- O uso de API não oficial do WhatsApp (Evolution/WAHA) segue as regras do WhatsApp; abuso pode bloquear o número.
- As cotas gratuitas do Google atendem pequenas empresas; volume muito alto pede Google Workspace.
- O cliente é o controlador dos dados dos contatos dele (LGPD). O sistema tem descadastro automático (SAIR).
