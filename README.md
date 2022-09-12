# Email Marketing

<aside>
📌 Esse é um compilado dos meus estudos e da minha experiência profissional com a criação de E-mail Marketing. Então além dos exemplos de código eu vou deixar aqui trecho e explicações sobre o funcionamento e até ondem eu consegui ir, claro que conforme eu for descobrindo novos detalhes vou ir atualizando por aqui 😊

</aside>

# 📰 Qual é a definição

E-mail Marketing é toda comunicação via e-mail que acontece entre uma empresa e seus contatos ou clientes. Uma campanha de E-mail Marketing pode ser desenvolvida em texto ou HTML e conter produtos, promoções, conteúdos etc. Em geral, as mensagens são enviadas com uma ferramenta de disparo de e-mails (Sales Force, Litmus, etc…).

A história do E-mail Marketing começou no fim da década de 1970, quando o gerente de marketing da Digital Equipment Corp, Gary Thuerk enviou 400 e-mails promovendo computadores da companhia, o que resultou em 13 milhões de dólares em vendas. Mas foi nos anos 1990 que a internet massificou o E-mail Marketing.

Para fazer um E-mail Marketing efetivo e não acabar na caixa de spam, é importante seguir as boas práticas. Isso abriu as portas para uma nova forma de comunicação, mas também fez surgir os indesejáveis spams e, por consequência, as regras para proteger os consumidores dessa prática.

Nos anos 2000, tornou-se claro que pensar que somente enviar e-mails, sem pensar no destinatário ou no conteúdo, não era suficiente. Desde então entende-se que, para fazer um E-mail Marketing efetivo e não acabar na caixa de spam, é importante seguir as boas práticas. O surgimento de tecnologias como os smartphones e de novas formas de relacionamento, como as redes sociais, teve impacto também sobre o E-mail Marketing. 

No entanto, independentemente da tecnologia, sabe-se que hoje é importante focar nas necessidades de cada usuário ao receber o e-mail. Assim, o que iniciou como comunicação de massa desenvolveu-se para uma estratégia de relacionamento com Leads e clientes.

# ❗A e**strutura do HTML de e-mail é diferente do HTML tradicional**

Isso significa que o que funciona em sites não necessariamente funcionará em E-mail Marketing, principalmente divs, sections, e folhas de estilo CSS externas, entre outras. 

A criação de E-mail Marketing muitas vezes é considerada complexa por ser um tipo específico, diferente de construção de HTML. A principal questão que a diferencia de HTML para sites é a forma de renderização: páginas da web sempre são renderizadas nos navegadores, enquanto o e-mail será renderizado de acordo com o cliente de e-mail – e cada um tem as suas regras.

Para acertar no e-mail, o ideal é simplificar. Ao invés de estruturas mais complexas, o ideal é usar tabelas inseridas dentro de tabelas e estilos em linha.

**Tabelas:** A estrutura de um e-mail é formada por tabelas, que serão o esqueleto da sua mensagem e darão forma a ela. Basicamente você usará três elementos:

`<table>` - A estrutura total que formará o seu template.

`<tr>` - As linhas da tabela.

`<td>` - Células da tabela, onde é possível incluir o conteúdo do seu e-mail.

Com a tag `<head>` da mensagem e o `<body>` construído em tabelas, você pode começar a criar um esqueleto da sua mensagem.

**Estilos:** Os estilos em E-mail Marketing são incluídos em linha. Isso significa que, ao invés de incluir os estilos em CSS na tag head, você deve incluir um atributo em cada elemento. O famoso CSS INLINE


```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;700&display=swap" rel="stylesheet">
    <title>Modelo</title>
		<!-- Aqui vai modificações não muito complexas para adaptar o responsivo ou tirar alguns pré estilo dos clientes-->
    <style type="text/css"> @media only screen and (max-width: 500px) {} </style>
</head>
<body>
    <center width="100%">
        <div width="100%" style="max-width: 640px;">
            <table width="100%" align="center" style="direction: rtl;max-width: 640px;" cellspacing="0"
                cellpadding="0" border="0">
										<!-- O conteudo vai aqui!-->
            </table>
        </div>
    </center>
</body>
</html>
```
# ❔ Comentários condicionais do Outlook

O Windows Outlook 2003 e superior usam o Microsoft Word como mecanismo de renderização, o que pode levar a alguns problemas de renderização estranhos. Os comentários condicionais do Outlook nos permitem adicionar bits de HTML que são lidos apenas pelas versões do Outlook baseadas no Word.

****Sintaxe básica:**** Podemos usar tags **MSO** ( **Micros oft Office** ) para adicionar HTML/CSS em qualquer lugar em um modelo de email . Este código será ignorado por outros clientes de e-mail. 

```html
<!--[if mso]>
    <table><tr><td>
        /* Outlook-specific HTML content goes here. */
    </td></tr></table>
<![endif]-->
```

Obs: Somente o Outlook renderizará esta tabela.

A principal maneira de usarmos tags MSO em nossos e-mails é criar “tabelas fantasmas” para que os e- [mails híbridos](https://stackoverflow.design/email/base/responsiveness#hybrid-design) não se desfaçam no Outlook. O design híbrido usa `inline-block`, `max-width`, `min-width`para empilhar colunas de tabela. O Outlook não oferece suporte a essas propriedades CSS, portanto, usamos tags MSO para criar “tabelas fantasmas” que aplicam uma largura fixa apenas para o Outlook. Sem a tabela fantasma acima, o Outlook exibiria a `<div>`largura de 100%.

### ****Versões do Outlook****

O uso de números de versão do Microsoft Office permite direcionar uma versão específica do Outlook.

| Outlook version(s) | Code |
| --- | --- |
| All Windows OutlookMost common | <!--[if mso]> your code <![endif]--> |
| Outlook 2000 | <!--[if mso 9]> your code <![endif]--> |
| Outlook 2002 | <!--[if mso 10]> your code <![endif]--> |
| Outlook 2003 | <!--[if mso 11]> your code <![endif]--> |
| Outlook 2007 | <!--[if mso 12]> your code <![endif]--> |
| Outlook 2010 | <!--[if mso 14]> your code <![endif]--> |
| Outlook 2013 | <!--[if mso 15]> your code <![endif]--> |
| Outlook 2016 | <!--[if mso 16]> your code <![endif]--> |

| Code | Description |
| --- | --- |
| gt | greater than |
| lt | less than |
| gte | greater than or equal to |
| lte | less than or equal to |
| | | or |
| ! | not |

### E o responsivo?

Todos os modelos de e-mail usam uma abordagem híbrida para reconfigurar o layout para diferentes tamanhos de tela em todos os clientes de e-mail (independentemente do suporte a consulta de mídia). Depois que uma linha de base compatível com dispositivos móveis é definida, as media queries podem ser usadas para aprimorar progressivamente os e-mails nos clientes que os suportam.

Depois que uma linha de base híbrida é definida, as consultas de mídia podem ser usadas para ajustar um layout de e-mail responsivo. Como as colunas (espero) já estão empilhadas, as consultas de mídia podem ser usadas para alterar a largura e o alinhamento do texto em pequenas janelas de visualização.

O design híbrido usa colunas de empilhamento de tabelas `inline-block`, `max-width`, `min-width`e [ghost](https://stackoverflow.design/email/base/mso#ghost-tables) sem consultas de mídia enquanto impõe uma largura de área de trabalho fixa para o Outlook.

```html
<tr>
    <td>
        <!--[if mso]>
        <table role="presentation" cellspacing="0" cellpadding="0" border="0" width="100%">
        <tr>
        <td width="340">
        <![endif]-->
            <div style="display:inline-block; width:100%; min-width:200px; max-width:340px;">
                Column 1
            </div>
        <!--[if mso]>
        </td>
        <td width="340">
        <![endif]-->
            <div style="display:inline-block; width:100%; min-width:200px; max-width:340px;">
                Column 2
            </div>
        <!--[if mso]>
        </td>
        </tr>
        </table>
        <![endif]-->
    </td>
</tr>
```

Neste exemplo, as duas colunas serão exibidas lado a lado em telas amplas de desktop e empilhadas uma sobre a outra em telas móveis estreitas.

### ****Espaçamento responsivo****

O preenchimento padrão da área de trabalho para modelos de email é **30px** . As classes de utilitário podem ser usadas para reduzir o espaçamento para **20px** ou **remover o preenchimento** em viewports menores. Útil para melhorar os layouts de e-mail no celular.

| Classe | Resultado |
| --- | --- |
| .sm-p-nenhum | preenchimento: 0; |
| .sm-pt-nenhum | topo de preenchimento: 0; |
| .sm-pb-nenhum | fundo de preenchimento: 0; |
| .sm-pr-nenhum | preenchimento direito: 0; |
| .sm-pl-nenhum | padding-esquerda: 0; |
| .sm-py-none | topo de preenchimento: 0; fundo de preenchimento: 0; |
| .sm-px-nenhum | preenchimento direito: 0; padding-esquerda: 0; |
| .sm-p | preenchimento: 20px; |
| .sm-pt | preenchimento superior: 20px; |
| .sm-pb | fundo de preenchimento: 20px; |
| .sm-pr | padding-right: 20px; |
| .sm-pl | padding-esquerdo: 20px; |
| .sm-py | preenchimento superior: 20px; fundo de preenchimento: 20px; |
| .sm-px | padding-right: 20px; padding-esquerdo: 20px; |
| .sm-mb | margem inferior: 20px; |

# 💌 Dicas e boas práticas para construção do e-mail

- Faça o e-mail em formato HTML e divida o conteúdo entre texto e imagens. A proporção ideal é de 40% de imagens e 60% texto. Dessa forma, suas taxas de entrega serão melhores e a leitura ficará mais fácil (seu e-mail fica mais leve e bem estruturado).
- Use a tag `alt` nas imagens, sempre colocando um texto que a descreva. É possível, inclusive, utilizar esse espaço para a área se encorajar a exibição da imagem, por exemplo, “eBook Introdução ao E-mail Marketing – Clique em ‘Autorizar imagens’ para visualizar.”
- Coloque links também nas imagens, pois, mesmo que elas não sejam exibidas, as áreas serão clicáveis. Essa prática é bastante útil quando se usa `alt` tags;
- CSS inline: Sempre utilize CSS inline junto as tags do código-fonte.
- Todas as imagens devem estar com atributo `border="0"`, isso faz com que o cliente de e-mail não coloque uma borda ao redor das imagens que tenham um link.
- Nova aba: Utilize sempre `target=”_blank”` nos links. Desta forma os links abrem sempre em uma nova aba, fazendo com que o leitor não abandone a janela atual.
- Espaçamento entre imagens: Por padrão, alguns clientes de e-mail adicionam cerca de 3px de espaçamento entre as imagens. Para solucionar este problema, basta inserir um atributo `display:block`, que irá remover esta lacuna entre as imagens.
- Distâncias: Os atributos `cellpadding`, `cellspacing` e `border` devem ser atribuídos pelo elemento, mesmo se for um valor nulo.
- Largura das imagens: Para garantir a visualização da mensagem em telas pequenas mantenha a largura das imagens do e-mail menor do que 500px. Sempre utilizar o `max-width` nas imagens, no caso de ícones pequenos usar o `min-witdth` para impedir que alguns clientes de e-mail, como o Outlook, deixem as imagens ainda menores.
- Fonte: Para determinar as fontes de seu template use `font-family`, pois a propriedade `font-face` funciona apenas em aparelhos que rodam iOS e no Apple Mail.

## Por que não transformar todo o e-mail em uma imagem?

A resposta para essa pergunta é simples: boa parte da sua lista não irá sequer vê-la. A maioria dos principais serviços de e-mail, como Hotmail, Yahoo! e Gmail, além do próprio Outlook, possuem um bloqueio padrão de segurança para exibição de qualquer formato de imagem que esteja em um e-mail. Com o nosso dia a dia cada vez mais abundante de informações, é raro que os usuários tenham disponibilidade de tempo e interesse a ponto de autorizarem a exibição para só então descobrirem do que o e-mail trata e verem se vale a pena clicar. Isso não funciona bem. É preciso que o e-mail mostre a que veio logo de cara. Ao usar apenas imagem, muitos destinatários irão ignorar o e-mail, deletá-lo ou marcá-lo como [spam](https://resultadosdigitais.com.br/blog/spam/).

# 💢 O que nunca fazer!

- Cada imagem deve pesar no máximo 100kB e você pode inserir até 470kB em imagens no seu layout: provedores não aceitam imagens acima de 100kB. Caso você envie um e-mail com imagens acima desse peso, elas não somente não serão abertas como irão prejudicar a entrega dos seus e-mails.
- Nunca utilize URLs relativas
- Evite utilizar uma única imagem grande como conteúdo do e-mail, pois isso é considerado como prática de SPAM.
- Não utilize `padding` na `<table>` ele não é reconhecido por todos os clientes de e-mail, sempre coloque na `<td>`
- Evite usar `iframe` em links de mensagens. Alguns provedores de e-mail não tratam da forma esperada. Utilize `<a hef="url_destino">Texto</a>.`
- Nunca utilize a tag `<link>` para referenciar um arquivo de estilos (.css), pois a maioria dos provedores removem essa tag
- Nem sempre as formas reduzida para definir um estilo são aceitas
- Não utilize a tag `<style>` como definição das classes de estilo, pois alguns provedores removem essa tag. Caso, insista em utilizar, coloque essa tag dentro da tag `<head>`, sendo necessário testar a mensagem em diversos clientes de e-mail, a fim de verificar se ela estará distorcida. Isso é usado principalmente no caso de **[Media Queries](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Media_Queries/Using_media_queries)**
- Evite utilizar `charset` no seu HTML, isso pode fazer com que alguns provedores desconfigurem o seu e-mail.
- Evite utilizar formulários pois estes são bloqueados no Outlook e por vários provedores.
- Nunca utilize Flash ou Javascript no corpo do e-mail, pois estes são bloqueados pelos antivírus dos principais provedores.
- Evite utilizar imagens de fundo, pois alguns provedores de e-mail não permitem a visualização da imagem, mas se usar Prefira utilizar a tag `<td background>`, por exemplo:
- Se precisar transformar o e-mail em OFT ou algo parecido, não usar o ltr pq vai ficar tudo invertido. Esses formulários gerados pelo Outlook tendem a desconfirgurar muitas coisas de estilos.

# 💠 Comentários sobre o código

- `head`
    - Eu uso esse padrão para todos os e-mails que crio, o que vai mudar é o titulo ou a fonte que vai ser importada. Lembrando que nem todos os clientes de e-mail aceitam o `link` então na tag `font` é sempre bom colocar uma fonte padrão como segunda opção.
    
    ```html
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;700&display=swap" rel="stylesheet">
        <title>Modelo ltr - responsivo</title>
        <style type="text/css"></style>
    </head>
    ```
    
    ```html
    <font class="font-mobile-text"
          style="font-family: 'Inter', sans-serif;font-size:16px;line-height:24px;letter-spacing:-0.2px;font-weight:400;color:#3D3D3D;">
               Texto Aqui                                                 
    </font>
    ```
    
- `style`
    - O CSS também não sofre muita mudança de um texto para o outro, mas é importante relembrar que o recomendado é o CSS inline, aqui eu coloco algumas configurações para tentar “limpar” o css que alguns clientes de e-mail colocam.
    - Na parte do `@media only screen and (max-width: 500px) {}` tem a tag `th` que deixa o ltr responsivo (só no caso do e-mail ltr) e as classes que centralizam. As demais são apenas ajustes de tamanho de texto, imagem e padding para melhorar a visualização no mobile. A falta delas não vai afetar o código que vai permanecer com o estilo definido pelo `style` na tag `font` de forma inline.
    - Lembrando que no caso do e-mail ser encaminhado, os clientes de e-mails retiram a tag `style` então o e-mail vai ficar com a forma de visualização como se estivesse sendo exibido em um navegador web (sem ser responsivo) no caso do ltr ou parcialmente responsivo mas desalinhado no caso do e-mail só com tabelas.
    - Código ltr
        
        ```css
        <style type="text/css">
                /* Configuração padrão */
                * {
                    -ms-text-size-adjust: 100%;
                    -webkit-text-size-adjust: 100%;
                }
        
                body {
                    margin: 0 auto !important;
                    padding: 0 !important;
                }
        
                table {
                    border-spacing: 0;
                }
        
                td {
                    padding: 0;
                }
        
                img {
                    border: 0;
                }
        
                table,
                td {
                    mso-table-lspace: 0pt !important;
                    mso-table-rspace: 0pt !important;
                    margin: 0 auto !important;
                }
        
                img {
                    -ms-interpolation-mode: bicubic;
                }
        
                *[x-apple-data-detectors],
                .x-gmail-data-detectors,
                .x-gmail-data-detectors *,
                .aBn {
                    border-bottom: 0 !important;
                    cursor: default !important;
                    color: inherit !important;
                    text-decoration: none !important;
                    font-size: inherit !important;
                    font-family: inherit !important;
                    font-weight: inherit !important;
                    line-height: inherit !important;
                }
        
             
                @media only screen and (max-width: 500px) {
        
                    /* faz o ltr */
                    th {
                        display: block !important;
                        width: 100% !important;
                    }
        
                    /* Tamanho de fontes */
                    .font-mobile-titleBig {
                        font-size: 24px !important;
                        line-height: 32px !important;
                    }
        
                    .font-mobile-title {
                        font-size: 20px !important;
                        line-height: 26px !important;
                    }
        
                    .font-mobile-subTitle {
                        font-size: 16px !important;
                        line-height: 24px !important;
                    }
        
                    .font-mobile-text {
                        font-size: 14px !important;
                        line-height: 20px !important;
                    }
        
                    .font-mobile-titleTable {
                        font-size: 20px !important;
                        line-height: 26px !important;
                    }
        
                    .font-mobile-footerTitle {
                        font-size: 14px !important;
                        line-height: 19px !important;
                    }
        
                    /* paddings internos */
        
                    .padding-mobile-blueTable {
                        padding: 32px !important;
                    }
        
                    .padding-mobile-iconsCanais {
                        padding-right: 32px !important;
                    }
        
                    .padding-mobile-hrFooter {
                        padding: 32px 0px !important;
                    }
        
                    .padding-top-banner {
                        padding-top: 16px !important;
                    }
        
                    .padding-bottom-banner {
                        padding-bottom: 23px !important;
                    }
        
                    .resposive-banner {
                        padding: 14px 34px !important;
                    }
        
                    .padding-ajuste {
                        padding-right: 0 !important;
                        padding-bottom: 32px !important;
                    }
        
                    .padding-zero {
                        padding: 0 !important;
                    }
                    .padding-icons {
                        padding-top: 24px !important;
                    }
        
                    .padding-icons-right {
                        padding-right: 50px !important;
                    }
        
                    /* altura */
                    .padding-mobile-height {
                        padding-top: 40px !important;
                    }
        
                    /* botão */
                    .button {
                        height: 44px !important;
                    }
        
                    .button-banner {
                        width: 150px !important;
                    }
        
                    .line-height-btn {
                        line-height: 40px !important;
                    }
        
                    /* centraliza o responsivo */
                    .centraliza {
                        float: none !important;
                    }
        
                    .text-center {
                        text-align: center !important;
                        padding-top: 0 !important;
                    }
        
                    /* img */
                    .logo-resposive {
                        width: 40px !important;
                    }
        
                    .img-responsive {
                        width: 140px !important;
                    }
        
                    .point {
                        width: 16px !important;
                        height: 16px !important;
                    }
                }
            </style>
        ```
        
    - Código sem ltr
        
        ```css
        <style type="text/css">
                /* Configuração padrão */
                * {
                    -ms-text-size-adjust: 100%;
                    -webkit-text-size-adjust: 100%;
                }
        
                body {
                    margin: 0 auto !important;
                    padding: 0 !important;
                }
        
                table {
                    border-spacing: 0;
                }
        
                td {
                    padding: 0;
                }
        
                img {
                    border: 0;
                }
        
                table,
                td {
                    mso-table-lspace: 0pt !important;
                    mso-table-rspace: 0pt !important;
                    margin: 0 auto !important;
                }
        
                img {
                    -ms-interpolation-mode: bicubic;
                }
        
                *[x-apple-data-detectors],
                .x-gmail-data-detectors,
                .x-gmail-data-detectors *,
                .aBn {
                    border-bottom: 0 !important;
                    cursor: default !important;
                    color: inherit !important;
                    text-decoration: none !important;
                    font-size: inherit !important;
                    font-family: inherit !important;
                    font-weight: inherit !important;
                    line-height: inherit !important;
                }
        
                @media screen and (max-width: 500px) {
        
                    /* Tamanho de fontes */
                    .font-mobile-title {
                        font-size: 24px !important;
                        line-height: 32px !important;
                    }
        
                    .font-mobile-subTitle {
                        font-size: 16px !important;
                        line-height: 24px !important;
                    }
        
                    .font-mobile-text {
                        font-size: 14px !important;
                        line-height: 20px !important;
                    }
        
                    .font-mobile-titleTable {
                        font-size: 20px !important;
                        line-height: 26px !important;
                    }
        
                    .font-mobile-footerTitle {
                        font-size: 13px !important;
                        line-height: 19px !important;
                    }
        
                    /* paddings internos */
        
                    .padding-mobile-blueTable {
                        padding: 32px !important;
                    }
        
                    .padding-mobile-iconsCanais {
                        padding-right: 32px !important;
                    }
        
                    .padding-mobile-hrFooter {
                        padding: 32px 0px !important;
                    }
        
                    /* altura */
                    .padding-mobile-height {
                        padding-top: 40px !important;
                    }
        
                    /* botão */
                    .button {
                        height: 44px !important;
                    }
        
                    /* centraliza o responsivo */
                    .centraliza {
                        float: none !important;
                    }
        
                }
            </style>
        ```
        
- `body`
    - A tag `body` é quem vai englobar todo o corpo do e-mail, mas a delimitação de tamanho é feita na `div` e depois na `table`.
    - Código ltr
        - Um detalhe é que começamos o e-mail com ltr com o `direction: rtl` que vai inverter o conteúdo, e nas demais `tables` vamos usar o `direction: ltr` para voltar com o direcionamento correto.
        
        ```html
        <body>
            <center width="100%">
                <div width="100%" style="max-width: 640px;">
                    <table width="100%" align="center" style="direction: rtl;max-width: 640px;" cellspacing="0"
                        cellpadding="0" border="0">
        										<!-- O conteudo vai aqui!-->
                    </table>
                </div>
            </center>
        </body>
        ```
        
    - Código sem Ltr
        
        ```html
        <body>
            <center width="100%">
                <div width="100%" style="max-width: 640px;">
                    <table width="100%" align="center" style="max-width: 640px;" cellspacing="0"
                        cellpadding="0" border="0">
        										<!-- O conteudo vai aqui!-->
                    </table>
                </div>
            </center>
        </body>
        ```
        
- `table`
    - Sempre que tivemos uma table ela deve ter a seguinte estrutura
    
    ```html
    <table width="100%" align="center" style="***" cellspacing="0" cellpadding="0" border="0"> </table>
    ```
    
    - A `table` aceita vários atributos, entretanto o `padding` e `margin` não funcionam em todos os clientes de email, então quando precisamos colocar espaçamento é sempre na `td`
    - Dentro da tabela principal sempre vamos colocar a seguinte estrutura (`tr>td`) para adicionar um novo “bloco” ao email
    
    ```html
    <!-- Quando o bloco precisar ser mais complexos (com mais divisões)-->
                    <tr>
                        <td>
                            <table width="100%"  cellspacing="0" cellpadding="0" border="0">
                                <tr>
                                    <td>
                                       <!-- Informação -->
                                    </td>
                                    <td>
                                       <!-- Informação -->
                                    </td>
                                </tr>
                            </table>
                        </td>
                    </tr>
    
    <!-- Bloco simples com um único componente -->
                    <tr>
                        <td>
                             <!-- Informação -->
                        </td>
                    </tr>
    ```
    
    - Código com tr>td>table
        - Se for um email com ltr basta adicionar `direction:ltr;` dentro do `style=""`
        
        ```html
        <!-- Textos -->
                        <tr>
                            <td style="padding-left: 40px;padding-right: 40px;">
                                <table width="100%" style="max-width: 520px;" cellspacing="0" cellpadding="0"
                                    border="0">
                                    <tr>
                                        <td>
                                            <font class="font-mobile-title"
                                                style="font-family: 'Inter', sans-serif;font-weight: bold;font-size: 32px;line-height: 40px;letter-spacing: -1.4 px;color: #4B6FDD;">
                                                Olá,
                                            </font>
                                            <font class="font-mobile-title"
                                                style="font-family: 'Inter', sans-serif;font-weight: bold;font-size: 32px;line-height: 40px;letter-spacing: -1.4 px;color: #757575;">
                                                %%nome%%
                                            </font>
                                            <br><br>
                                            <font class="font-mobile-text"
                                                style="font-family: 'Inter', sans-serif;font-weight: normal;font-size:16px;line-height: 24px;letter-spacing: -0.2 px;color: #3D3D3D;">
                                               Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras a est diam. Integer hendrerit ipsum at ex interdum aliquam. Proin sed pellentesque enim. 
        																			Praesent metus ipsum, vestibulum ac sem at, <b> dictum pharetra eros.</b> 
                                        </td>
                                    </tr>
                                </table>
                            </td>
                        </tr>
        ```
        
    - Código com tr>td
        
        ```html
        <!-- Banner -->
                        <tr>
                            <td>
                                <img src="#"
                                    width="640" style="max-width: 100%;"
                                    alt="descrição do Banner">
                            </td>
                        </tr>
        <!-- espaço -->
                        <tr>
                            <td class="padding-mobile-height" style="padding-top: 56px;"></td>
                        </tr>
        ```
        
- `tr` e `td`
    - Como estamos programando em tabelas, sempre vamos usar a estrutura de `tr>td`dentro da `table` principal, sempre imaginando uma tabela e com a definição inicial foi dentro de uma linha (`tr`) vai ter uma célula (`td`), precisamos seguir esse esquema até o fim, ao contrário o código vai “quebrar”.
    - Se precisarmos de uma bloco de conteúdo com mais de uma célula vamos usar a estrutura de `tr>td>table` . Dentro dessa nova `table` funciona a mesma regra, todas a `tr` subsequentes a primeira precisam ter o mesmo número de `td`, já que é uma tabela afinal.
    - Existe uma forma de ignorar isso que não dever ser usada sempre pois pode deixar o código mais suscetível a quebras. **`Rowspan`** e **`colspan`** servem para expandir as células fazendo com que uma única célula ocupe mais de uma linha ou mais de uma coluna. Exemplo:
    
    ```html
    <!-- Tabela azul -->
    <tr>
        <td style="padding: 0 24px;">
            <table width="100%" style="direction: ltr;max-width: 576px;" cellspacing="0" cellpadding="0" border="0">
    			<!-- uma tr com 2 tds-->
                <tr>
                    <td valign="top" style="padding-right: 5px;">
                        <img class="point"
                            src="https://image.relacionamento.bv.com.br/lib/fe3b157175640475751579/m/731/63342454-8761-463f-80f9-2d86afa11d7d.png"
                            alt="folha" width="24" height="25" style="min-width: 24px;min-height: 25px;">
                    </td>
                    <td style="padding-bottom: 24px;">
                        <font class="font-mobile-text"
                            style="font-family: 'Inter', sans-serif;font-size:16px;line-height:24px;letter-spacing:-0.2x;font-weight:400;color:#3D3D3D;">
                            Desconto direto em folha de pagamento
                        </font>
                    </td>
                </tr>
    <!-- uma tr com o colspan="2" referente ao numero de tds que aquela tr deveria ter -->
                <tr>
                    <td colspan="2" align="center" style="max-width: 512px;" width="512">
                        <table align="center" cellspacing="0" cellpadding="0" border="0">
                            <tr>
                                <td class="button" align="center" width="210" height="56"
                                    style="background-color:#4B6FDD;border-radius:8px;box-sizing: border-box;">
                                    <a href="https://www.bv.com.br/consignado/consignado-privado/v2?idcmp=T03|C02|V49|F87|P203|AQ|150114149680-20220506|CLIENTES_CREDITO_CONSIGNADO|PAP_MAIO_2Q_PPR_052022|EMAIL_CTA_CLIQUE_PARA_SIMULAR_CLIENTES_CREDITO_CONSIGNADO_PAP_MAIO_2Q_PPR_D1_NOVOS_AUTOSSERVICO_REDIRECT_SITEBV"
                                        target="_blank"
                                        style="font-weight:bold;font-family:'Inter', Helvetica, sans-serif;color:#FFFFFF;display:inline-block;text-decoration:none;line-height:60px;width:210px;font-size: 16px;">
                                        Clique para simular!</a>
                                </td>
                            </tr>
                        </table>
                    </td>
                </tr>
    			</table>
    	</td>
    <tr>
    ```
    
    - A `tr` não aceita nenhum atributo, eles podem até funcionar quando estamos visualizando no navegado enquanto programamos, mas ao enviar o e-mail tudo será desconsiderado.
    - A `td` pode ficar sem nenhum ou ter vários atributos, o principal é que atributos com `padding` (`margin` não é indicado) e `valign` só funcionam em `td`.
- bloco responsivo
    - A forma de fazer um e-mail marketing responsivo é forçando um tamanho máximo (max-width) para a table/th e obrigando esses bloco a descerem quando o tamanho for menor que a soma da largura dos blocos.
    - Os dois tipos de código que eu tenho tem um `@media only screen and (max-width: 500px) {}` que já é o tamanho de alguns tablets, levando em conta que o e-mail marketing não deve passar dos 700px de largura.
    - No caso do modelo ltr que usa `th` , quando chegar aos 500px ele vai ficar com o `display:block;` e o `width: 100%;`, isso faz com que as `th` ocupem todo o espaço da tela ficando empilhadas.
    - No modelo que não utiliza o ltr não tem nenhuma classe que faça o responsivo, ele funcional como descrevi acima, o `max-width` da `table`obriga os bloco a descerem quando o tamanho for menor que a soma da largura dos blocos.
    - Nos dois modelos tem as classes que vão deixar os blocos centralizados
    
    ```css
    /* centraliza o responsivo */
                .centraliza {
                    float: none !important;
                }
    
                .text-center {
                    text-align: center !important;
                    padding-top: 0 !important;
                }
    ```
    
    - Código responsivo (modelo sem ltr)
        
        ```html
        <!--bloco responsivo -->
                        <tr>
                            <td>
                                <table cellspacing="0" cellpadding="0" border="0" style="max-width: 576px;padding: 0 40px;"
                                    align="center">
                                    <tr>
                                        <td valign="top">
                                            <table class="centraliza" cellspacing="0" cellpadding="0" border="0"
                                                style="max-width: 120px;padding-right: 32px;" align="left">
                                                <tr>
                                                    <td valign="top">
                                                        <img src="#"
                                                            alt="dercrição da imagem" width="120" 
                                                            style="max-width: 120px;min-width: 120px;">
                                                    </td>
                                                </tr>
                                            </table>
                                            <table cellspacing="0" cellpadding="0" border="0" style="max-width: 360px;"
                                                align="center">
                                                <tr>
                                                    <td style="padding-top:20px">
                                                        <font class="font-mobile-subTitle"
                                                            style="font-family: 'Inter', sans-serif;font-weight: normal;font-size:20px;line-height: 26px;letter-spacing: -0.56px;color: #3D3D3D;">
                                                           Lorem ipsum dolor sit amet,
                                                        </font>
                                                    </td>
                                                </tr>
                                            </table>
                                        </td>
                                    </tr>
                                </table>
                            </td>
                        </tr>
        ```
        
- `th`
    - Normalmente um `th` define uma célula cabeçalho do grupo de células de sua tabela
    - Ela pode ser usada no modelo de código sem ltr com a sua função normal, já que ela se comporta como uma `td` normal
    - No modelo ltr a `th` é que é responsável pelos blocos responsivos (pode se usar o modelo responsivo com `table` no ltr que também vai funcionar, mas o contrário não é valido), então ela tem um comportamento de uma `table` e uma td ao mesmo tempo
    - Exemplo de utilização (é sempre em bloco responsivo):
        - Código com direção dos blocos normal
            
            ```html
            <!-- bloco responsivo -->
                            <tr>
                                <td style="padding: 0 40px;" align="left">
                                    <table cellspacing="0" cellpadding="0" border="0" style="direction:ltr;max-width: 576px;"
                                        align="left" class="centraliza">
                                        <tr>
                                            <td align="left" style="padding: 0 28px;" class="padding-zero">
                                                <table align="left" cellspacing="0" cellpadding="0" border="0">
                                                    <tr>
            																		<!-- aqui a th fica como se fosse a table no modelo de código sem ltr -->
                                                        <th width="184" border="0" style="direction: ltr;" valign="top">
            																						<!-- a th precisa de table dentro -->
                                                            <table class="centraliza" cellspacing="0" cellpadding="0" border="0"
                                                                style="max-width: 184px;" align="left">
                                                                <tr>
                                                                    <td style="padding-right: 32px;" class="padding-ajuste">
                                                                        <img src="#"
                                                                            alt="descrição" width="184"
                                                                            style="min-width: 140px;" class="img-responsive">
                                                                    </td>
                                                                </tr>
                                                            </table>
                                                        </th>
                                                        <th width="306" border="0" style="direction: ltr;">
                                                            <table class="centraliza" cellspacing="0" cellpadding="0" border="0"
                                                                style="max-width: 376px;" align="left">
                                                                <tr>
                                                                    <td align="left" style="display:flex;padding-bottom: 16px;">
                                                                        <img src="https://image.relacionamento.bv.com.br/lib/fe3b157175640475751579/m/29/f44b7017-5a53-49b2-abdc-9c7eb4fb77c9.png"
                                                                            alt="haste azul" height="27" style="max-height: 27px;">
                                                                        <font class="font-mobile-titleTable"
                                                                            style="font-family: 'Inter', sans-serif; color:#4B6FDD;font-size:24px;line-height:32px;letter-spacing:-0.6px;font-weight:bold;text-align: left;margin-left: 4px;">
                                                                          Lorem Ipsum
                                                                        </font>
                                                                    </td>
                                                                </tr>
                                                                <tr>
                                                                    <td align="left">
                                                                        <font class="font-mobile-subTitle"
                                                                            style="font-family: 'Inter', sans-serif;font-weight: normal;font-size:20px;line-height: 26px;letter-spacing: -0.56px;color: #3D3D3D;">
                                                                            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras a est diam. Integer hendrerit ipsum at ex interdum aliquam. Proin sed pellentesque enim.
                                                                        </font>
                                                                        <br><br>
                                                                        <font class="font-mobile-text"
                                                                            style="font-family: 'Inter', sans-serif;font-weight: normal;font-size:16px;line-height: 24px;letter-spacing: -0.2 px;color: #3D3D3D;">
                                                                           Lorem ipsum dolor sit amet, 
                                                                        </font>
                                                                    </td>
                                                                </tr>
                                                            </table>
                                                        </th>
                                                    </tr>
                                                </table>
                                            </td>
                                        </tr>
                                    </table>
                                </td>
                            </tr>
            ```
            
        - Código com direção dos blocos invertida
            
            ```html
            <!-- Bloco responsivo "ao contrario"  -->
                            <tr>
                                <td style="padding: 0 40px;">
                                    <table cellspacing="0" cellpadding="0" border="0" style="max-width: 510px;">
                                        <tr>
                                            <th width="184" border="0" style="direction: ltr;" valign="top">
                                                <table class="centraliza" cellspacing="0" cellpadding="0" border="0"
                                                    style="max-width: 184px;" align="left">
                                                    <tr>
                                                        <td style="padding-bottom: 32px;">
                                                            <img src="#"
                                                                alt="descrição" width="184" style="min-width: 120px;"
                                                                class="img-responsive">
                                                        </td>
                                                    </tr>
                                                </table>
                                            </th>
                                            <th width="320" border="0" style="direction: ltr;">
                                                <table class="centraliza" cellspacing="0" cellpadding="0" border="0"
                                                    style="max-width: 368px;" align="left">
                                                    <tr>
                                                        <td align="left" style="display:flex;padding-bottom: 24px;">
                                                            <img src="https://image.relacionamento.bv.com.br/lib/fe3b157175640475751579/m/29/f44b7017-5a53-49b2-abdc-9c7eb4fb77c9.png"
                                                                alt="haste azul" height="27" style="max-height: 27px;">
                                                            <font class="font-mobile-titleTable"
                                                                style="font-family: 'Inter', sans-serif; color:#2142AB;font-size:24px;line-height:32px;letter-spacing:-0.6px;font-weight:bold;text-align: left;margin-left: 4px;">
                                                               Lorem Ipsum
                                                            </font>
                                                        </td>
                                                    </tr>
                                                    <tr>
                                                        <td>
                                                            <table cellspacing="0" cellpadding="0" border="0" align="left">
                                                                <tr>
                                                                    <td align="left" valign="top" class="padding-zero">
                                                                        <img src="#"
                                                                            alt="descrição" height="24"
                                                                            style="max-width: 24px;min-width: 24px;min-height: 24px;">
                                                                    </td>
                                                                    <td align="left"
                                                                        style="padding-left: 8px;display: flex;padding-bottom: 24px;">
                                                                        <font class="font-mobile-text"
                                                                            style="font-family: 'Inter', sans-serif;font-size:16px;line-height:24px;letter-spacing:0.3px;font-weight:400;color:#3D3D3D;">
                                                                           Lorem ipsum dolor sit amet,
                                                                        </font>
                                                                    </td>
                                                                </tr>
                                                            </table>
                                                        </td>
                                                    </tr>
                                                </table>
                                            </th>
                                        </tr>
                                    </table>
                                </td>
                            </tr>
            ```
            
    - Quando temos um bloco com duas `td`  e que não vai ser responsivo é preciso “englobar” ele em uma `table`, pois alguns clientes de e-mail (principalmente os instalados no computador) invertem esse blocos mesmo com o `style=”direction:ltr;”` .
        - Exemplo do caso acima:
            
            ![Untitled](Email%20Marketing%20574ec000f024412ab0eaafeaeb76991f/Untitled%201.png)
            
            ```html
            <!-- info azul -->
                            <tr>
                                <td style="padding: 0 24px;">
                                    <table width="100%" style="direction: ltr;max-width: 576px;" cellspacing="0" cellpadding="0"
                                        border="0">
                                        <tr>
                                            <td class="padding-mobile-blueTable"
                                                style="background-color: #F4F7FE;padding: 32px;border-bottom-right-radius: 16px;border-top-left-radius: 16px;">
                                               <!-- a table englobando -->
            																	 <table cellspacing="0" cellpadding="0" border="0" style="max-width: 512px;">
                                                    <tr>
                                                        <td align="left">
                                                            <table cellspacing="0" cellpadding="0" border="0">
                                                                <tr>
                                                                    <td valign="top">
                                                                        <img src="https://image.relacionamento.bv.com.br/lib/fe3b157175640475751579/m/384/a9227dbd-945b-4ae7-859b-6c9ea19bb79c.png"
                                                                            alt="celular" width="87" style="min-width: 87px;">
                                                                    </td>
                                                                    <td align="left" style="padding-left: 24px;">
                                                                        <font class="font-mobile-text"
                                                                            style="font-family: 'Inter', sans-serif; color:#4B6FDD;font-size:20px;line-height:26px;letter-spacing:-0.66px;font-weight:bold;text-align: left;">
                                                                            Para facilitar a abertura da sua conta, <font
                                                                                style="color:#3D3D3D;font-weight: normal;">
                                                                                tenha seus documentos sempre em mãos!</font>
                                                                        </font>
                                                                    </td>
                                                                </tr>
                                                            </table>
                                                        </td>
                                                    </tr>
                                                </table>
                                            </td>
                                        </tr>
                                    </table>
                                </td>
                            </tr>
            ```
            
- Outros detalhes
    - Se precisar colocar alguma tag de rastreio ela deve ser coloca da logo após a abertura da tag `body` ou antes do fechamento da tag `body`
    
    ```html
    <body>
        <custom name="opencounter" type="tracking" />
    
    		<!--conteudo do email-->
    
        <img src="https://pixel.app.returnpath.net/pixel.gif?r=30eafaafc1044673aa68637078183c59cd2e6c24&c=%%emailname_%%&s=%%subscriberid%%"
            width="1" height="1" />
    </body>
    ```
    
    - Não colocar links grandes no e-mail, o link não quebra de linha e vai acabar forçando um tamanho que vai atrapalha a responsividade ou até mesmo ultrapassar os pixels ideias de largura da visualização web.

## Usar ltr ou não?

<aside>
📌 O ltr é principalmente usado quando vamos ter a necessidade de uma inversão de direção em algum bloco de código, entretanto é o modelo que eu prefiro usar por conta de funcionar muito bem no responsivo, também é um código que dificilmente vai apresentar quebras por questão de largura nos blocos. Um detalhe no ltr é que se precisar transformar o e-mail em algum modelo do Outlook (.oft .msg), ele vai ficar completamente invertido, então não é indicado nesse caso.

</aside>
<br>
<aside>
📌 O modelo que é só tabelas as vezes apresenta quebras em tamanho próximos ao breakpoint do mobile (510px, 504px) e acaba quebrando mesmo tendo espaço, isso porque ele parece ter a necessidade de ter alguns pixels de “sobra” entre os blocos, coisa que não é necessária no modelo ltr que se adapta melhor na telas.

</aside>
<br>
<aside>
📌 **No fim os dois modelos funcionam bem, cada um com a sua particularidade que deve ser levada em conta dependendo da complexidade do e-mail que vai ser feito. Dito isso, é só pegar os código e programar** ❤

</aside>
# ⚙Links de apoio

Vários links que eu uso para consulta vez ou outra, tem muita informação em fóruns também. 

- [https://templateria.com.br/blog/templates/50-fatos-sobre-email-marketing-no-outlook/](https://templateria.com.br/blog/templates/50-fatos-sobre-email-marketing-no-outlook/)
- [https://stackoverflow.design/email/base/mso/](https://stackoverflow.design/email/base/mso/)
- [https://www.htmlemailcheck.com/knowledge-base/target-outlook-email-clients-using-conditional-comments/](https://www.htmlemailcheck.com/knowledge-base/target-outlook-email-clients-using-conditional-comments/)
- [https://www.emailonacid.com/tip/outlook-desktop/](https://www.emailonacid.com/tip/outlook-desktop/)
- [https://litmus.com/community/discussions/516-outlook-com-stripping-conditional-comments-try-this](https://litmus.com/community/discussions/516-outlook-com-stripping-conditional-comments-try-this)
- [https://www.emailonacid.com/blog/article/email-development/emailology_vector_markup_language_and_backgrounds/](https://www.emailonacid.com/blog/article/email-development/emailology_vector_markup_language_and_backgrounds/)
- [https://www.hteumeuleu.com/](https://www.hteumeuleu.com/)
- [https://github.com/hteumeuleu](https://github.com/hteumeuleu)
- [https://litmus.com/community/](https://litmus.com/community/)
- [https://www.campaignmonitor.com/](https://www.campaignmonitor.com/)
- [https://proofjump.com/dark-mode-simulator/](https://proofjump.com/dark-mode-simulator/)
- [https://www.campaignmonitor.com/css/color-background/background-image/](https://www.campaignmonitor.com/css/color-background/background-image/)
