# Guia do vendedor (uso interno, não vai para o cliente)

Esta pasta é separada do produto. Aqui fica o que é seu: página de vendas, links de pagamento, o gerador de código de suporte e o processo de entrega. O produto (`prumo-crm`) é entregue limpo, sem nada daqui.

## Planos

O sistema é o mesmo nos três planos e o cliente fica com ele para sempre. O que muda é o tempo de suporte e atualizações:

| Plano | Suporte e atualizações | Preço sugerido na página |
|---|---|---|
| Essencial | 1 mês | R$ 997 |
| Anual | 1 ano | R$ 1.497 |
| Cinco anos | 5 anos | R$ 2.497 |

Os preços são sugestões; troque à vontade. Na página, o plano Anual já aparece selecionado.

**Order bump:** se o checkout (Mercado Pago, Hotmart, Kiwify) permitir, venda o Essencial como produto principal e ofereça a troca para o Anual ou o Cinco anos como order bump, pagando a diferença. Na página, cada plano já tem o seu botão.

**Deixe claro na venda:** sem suporte ativo o sistema continua funcionando, mas sem atualizações. Integrações de terceiros (Meta, Google, Mercado Pago, Evolution) mudam com o tempo e podem precisar de atualização. O cliente lê a mesma explicação em `docs/SUPORTE_E_ATUALIZACOES.md` e dentro do sistema.

## Código de suporte (para cada comprador)

Abra `privado/gerar-codigo-suporte.html` no navegador (ele roda só no seu computador e não vai para o GitHub). Preencha o nome do comprador, o plano, a data da compra e o seu contato de suporte. A validade é calculada sozinha. Copie o código e envie junto com a entrega.

O cliente cola o código em **Ajustes > Sistema > Plano de suporte**. O sistema passa a mostrar o plano, a validade e o seu contato, e avisa o administrador 15 dias antes do fim e quando acaba. Assim o pacote continua sem nenhuma informação sua: o seu contato vai só no código. Quando alguém renovar, gere um código novo com a nova data.

## Modelo de entrega

O cliente recebe tudo e fica dono de tudo:

1. **Planilha pronta** (link `/copy`): ao abrir, ele faz uma cópia na conta Google dele, com o script dentro.
2. **Pacote limpo** (`prumo-crm-vX.Y.Z.zip`): pasta `site` para subir no GitHub dele, `planilha/Codigo.gs` e os guias.
3. **Vídeos**: montar o script na planilha, publicar o Apps Script e subir o site no GitHub Pages. O roteiro segue o `docs/INSTALACAO.md`.
4. **Código de suporte** do plano comprado.

Nenhum servidor seu fica no caminho. Se você parar de vender amanhã, o cliente continua usando.

## Gerar o pacote limpo

Na pasta do produto:

```bash
node ferramentas/empacotar.js
```

Gera `prumo-crm/dist/prumo-crm-vX.Y.Z.zip` sem histórico do git, sem testes e sem informações suas (o comando confere e para se achar algo pessoal).

## Criar a planilha-modelo (uma vez por versão)

1. Crie uma planilha em branco numa conta Google só do produto (a cópia mostra ao cliente quem é o dono da original), com um nome neutro, por exemplo "Prumo CRM".
2. Extensões > Apps Script > cole o `planilha/Codigo.gs` do pacote > salve. **Não rode o instalar** (quem instala é o cliente, com o e-mail dele).
3. Compartilhar > Qualquer pessoa com o link > Leitor.
4. Troque o final do link de `/edit...` por `/copy`:
   `https://docs.google.com/spreadsheets/d/ID_DA_PLANILHA/copy`

## Página de vendas

`index.html` desta pasta. Antes de divulgar, preencha no fim do arquivo, em `PLANOS`:

- `preco` de cada plano;
- `link` de pagamento de cada plano (Mercado Pago: Seu negócio > Link de pagamento; ou o checkout da Hotmart/Kiwify). Sem link, o botão avisa que o pagamento não foi configurado;
- `parcelas` (opcional): por exemplo "ou 12x no cartão", só se o seu checkout oferecer;
- `LINK_DEMO`: a demonstração já aponta para o seu GitHub Pages. `&entrar=1` entra direto e `&nome=` e `&cor=` abrem com a marca do visitante (a página usa isso no bloco "Com a cara da sua empresa" e na frase do final);
- `PRECO_BARRA`: o valor usado na última barra da conta da mensalidade.

As telas da seção "Tudo numa tela só" são capturas reais da demonstração, em `assets/telas`. Para atualizar depois de uma versão nova, rode na pasta do produto um servidor local e capture de novo (o comando está no histórico do projeto).

A foto do prumo é de Salil Kumar Mukherjee (CC BY-SA 4.0, Wikimedia Commons); o crédito está no rodapé da página.

## Termos para deixar claros na venda

- O uso de API não oficial do WhatsApp (Evolution/WAHA) segue as regras do WhatsApp; abuso pode bloquear o número.
- As cotas gratuitas do Google atendem pequenas empresas; volume muito alto pede Google Workspace.
- O cliente é o controlador dos dados dos contatos dele (LGPD). O sistema tem descadastro automático no WhatsApp e no e-mail.
