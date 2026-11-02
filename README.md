# LexScan Imóveis

Aplicação web local para triagem de contratos imobiliários, com foco em:

- contratos de locação de imóveis;
- contratos de compra e venda de imóveis.

O sistema analisa o texto do contrato, identifica possíveis omissões e expressões vagas, apresenta alertas de completude e redação e sugere alterações no parágrafo completo. A aplicação também permite exportar o relatório de triagem em Word.

> **Aviso:** o LexScan Imóveis é uma ferramenta educacional e heurística. Não emite parecer jurídico, não confirma validade ou nulidade de cláusulas e não substitui a análise de advogado ou profissional habilitado.

## Funcionalidades

- Seleção entre contrato de locação e contrato de compra e venda.
- Importação de arquivos TXT, PDF e DOCX.
- Colagem e edição manual do texto do contrato.
- Contagem de caracteres.
- Análise de completude contratual.
- Identificação de expressões potencialmente vagas.
- Exibição do parágrafo original completo.
- Exibição do parágrafo completo sugerido.
- Preservação das quebras de linha na apresentação dos resultados.
- Inserção de linha em branco antes de itens numerados, como `01`, `02`, `2.2`, `2.3` e `2.4`.
- Indicadores de completude, redação e atenção jurídica.
- Salvamento local do último contrato analisado.
- Restauração automática do último contrato ao reabrir a página.
- Botão **Limpar** para apagar o contrato salvo e iniciar outra análise.
- Exportação do relatório em Word, no formato DOCX.
- Tema escuro e interface responsiva.
- Processamento no navegador, sem envio intencional do conteúdo do contrato para um servidor de análise.

## Como executar

1. Baixe o arquivo `index.html`.
2. Mantenha uma conexão com a internet para o carregamento das bibliotecas externas.
3. Abra o arquivo em um navegador moderno, como Microsoft Edge, Google Chrome ou Firefox.
4. Selecione o tipo de contrato.
5. Importe um arquivo ou cole o conteúdo no campo **Texto do contrato**.
6. Clique em **Revisar contrato**.
7. Consulte o relatório de triagem.
8. Clique em **Baixar Word** para gerar o relatório em DOCX.

Não é necessário instalar servidor, banco de dados ou dependências localmente.

## Formatos aceitos

| Formato | Observação |
|---|---|
| TXT | Texto simples. |
| PDF | Deve possuir texto selecionável. PDFs digitalizados podem exigir OCR antes da importação. |
| DOCX | O texto é extraído diretamente no navegador. |

## Critérios de análise

### Locação de imóvel

A triagem procura elementos relacionados a:

- identificação do locador, locatário e imóvel;
- aluguel, vencimento e reajuste;
- prazo, vigência e entrega de chaves;
- garantia locatícia;
- vistoria, conservação, reparos e benfeitorias;
- rescisão e proporcionalidade da multa.

### Compra e venda de imóvel

A triagem procura elementos relacionados a:

- identificação do vendedor, comprador e imóvel;
- matrícula e cartório competente;
- preço, sinal, parcelas e condições de pagamento;
- certidões, tributos e ônus;
- escritura, registro e transferência;
- posse e entrega de chaves;
- inadimplemento, rescisão e distrato.

## Relatório de triagem

O relatório apresenta três indicadores preliminares:

- **Completude:** presença de elementos essenciais cadastrados no motor de análise.
- **Redação:** ocorrência de expressões potencialmente vagas.
- **Atenção jurídica:** temas que merecem conferência profissional.

Quando uma expressão vaga é encontrada, o relatório exibe:

1. a localização aproximada do parágrafo;
2. o parágrafo original completo;
3. o parágrafo completo com a sugestão de redação;
4. campos entre colchetes que devem ser preenchidos com dados objetivos do negócio.

Os indicadores são heurísticos e não representam aprovação, reprovação ou conclusão jurídica sobre o contrato.

## Persistência local

O último contrato e o tipo selecionado são armazenados no `localStorage` do navegador.

Ao reabrir a página no mesmo navegador:

- o último contrato é restaurado;
- o tipo de contrato é recuperado;
- a análise é executada novamente quando o texto possui tamanho suficiente.

O botão **Limpar** remove os dados salvos, limpa a interface e prepara a aplicação para um novo contrato.

## Exportação para Word

O botão **Baixar Word** gera um arquivo chamado:

```text
relatorio-lexscan-imoveis.docx
```

O documento inclui:

- título do relatório;
- resumo da análise;
- indicadores de pontuação;
- achados numerados;
- referências associadas ao apontamento;
- parágrafo original;
- parágrafo sugerido;
- aviso de caráter educacional.

## Dependências externas

O arquivo HTML carrega bibliotecas externas por CDN:

- **PDF.js 3.11.174:** leitura de PDFs com texto selecionável;
- **Mammoth.js 1.12.1:** extração de texto de arquivos DOCX;
- **html-docx-js 0.3.1:** geração do relatório em Word.

Se alguma dessas bibliotecas não for carregada, a funcionalidade correspondente poderá ficar indisponível.

## Privacidade

A análise e o armazenamento do contrato ocorrem no navegador. O texto permanece no dispositivo por meio do armazenamento local do navegador, até que o usuário clique em **Limpar**, apague os dados do site ou utilize outra sessão ou navegador.

As bibliotecas externas são carregadas pela internet. Para contratos com informações sensíveis, avalie as políticas de segurança do ambiente e das redes utilizadas.

## Referências jurídicas exibidas pela aplicação

A interface inclui links para conferência de:

- Lei do Inquilinato, Lei nº 8.245/1991;
- Código Civil;
- Lei de Registros Públicos;
- Lei de Condomínios e Incorporações;
- Lei nº 13.786/2018, quando aplicável ao distrato imobiliário.

As referências servem como ponto de partida para conferência. A aplicação não verifica automaticamente alterações legislativas nem substitui pesquisa jurídica atualizada.

## Estrutura do projeto

```text
/
├── index.html
└── README.md
```

Toda a interface, os estilos e o motor de análise estão reunidos no arquivo `index.html`.

## Limitações conhecidas

- A análise é baseada em palavras-chave e regras heurísticas.
- A ferramenta pode produzir falsos positivos ou deixar de identificar questões relevantes.
- A extração de PDF depende da estrutura interna do documento.
- PDFs compostos apenas por imagens não são processados sem OCR.
- A formatação original de documentos complexos pode não ser reproduzida integralmente.
- As sugestões contêm campos como `[●]`, que precisam ser preenchidos manualmente.
- A exportação para Word depende do carregamento da biblioteca externa correspondente.

## Uso responsável

Antes de assinar ou alterar um contrato:

- confira os dados das partes e do imóvel;
- valide matrícula, certidões, tributos e eventuais ônus;
- confirme valores, índices, prazos e responsabilidades;
- revise as sugestões conforme o contexto real do negócio;
- solicite análise de profissional habilitado.

### Instalação no computador

### No Google Chrome ou Microsoft Edge:

  1. Abra o endereço publicado do projeto.
  2. Aguarde o carregamento completo da página.
  3. Clique no ícone de instalação exibido na barra de endereço ou abra o menu do navegador.
  4. Selecione Instalar aplicativo ou Instalar este site como aplicativo.
  5. Confirme a instalação.

Depois disso, o aplicativo poderá ser aberto pelo menu Iniciar, pela área de trabalho ou pelo gerenciador de aplicativos do sistema.

### Instalação no celular ou tablet

### Em navegadores compatíveis:

1. Abra o endereço do projeto.
2. Acesse o menu do navegador.
3. Selecione Instalar aplicativo ou Adicionar à tela inicial.
4. Confirme o nome e a instalação.

O ícone será adicionado à tela inicial do dispositivo.

**Observações**

A disponibilidade e o nome da opção de instalação podem variar conforme o navegador e o sistema operacional.
Abrir somente o arquivo index.html pelo computador não garante a instalação como PWA.
O projeto deve ser publicado em HTTPS para utilizar os recursos completos de instalação e service worker.
O funcionamento offline depende da configuração do service-worker.js e dos arquivos adicionados ao cache.
Atualizações no projeto podem exigir a atualização da versão do cache do service worker.

## Licença

Nenhuma licença específica foi definida no arquivo fornecido. Antes de distribuir ou publicar o projeto, inclua uma licença compatível com a finalidade pretendida e verifique as licenças das bibliotecas externas utilizadas.


## Aviso

> Este projeto é uma demonstração educacional desenvolvida para estudos de HTML, CSS e JavaScript. A empresa mencionada é fictícia e qualquer semelhança com empresas reais é mera coincidência.

