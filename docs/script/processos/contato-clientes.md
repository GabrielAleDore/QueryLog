---
tags:
    - script
    - processos
icon: lucide/Smartphone
---
# Contato com Clientes

### Orientações de Comunicação com o Cliente
A comunicação com o cliente pode variar de acordo com a situação e a ferramenta utilizada. O principal objetivo durante a resolução da demanda é garantir que o cliente esteja ciente do processo e das ações tomadas, documentando todo o histórico de interações.

### Canal de Comunicação
Se a demanda estiver sendo tratada via chat, todo o contato com o cliente deve continuar nesse meio. O chat é utilizado principalmente para documentar o ticket e encaminhá-lo ao time comercial para análise de custos.

### Retorno do Chamado
Caso o cliente não tenha respondido no chat, será necessário utilizar um canal direto, como WhatsApp ou outro meio de contato preferencial do cliente, para garantir que a comunicação seja eficaz.

### Tentativas de Contato
Por padrão, são realizadas **três tentativas de contato** com o cliente. Se, após essas tentativas, o cliente não fornecer um retorno, o ticket será finalizado.

!!! info "Abaixo, você encontrará os modelos de **mensagens padrões** para cada situação, bem como as **mensagens específicas** para as três tentativas de contato com o cliente"

## Templates e Menssagens padrões

### Serviço cobrado:
>Gostaríamos de lembrá-lo que a próximo passo da atividade tem um custo associado. Se você quiser continuar com a atividade, por favor, digite “sim” no chat. Isso será considerado como uma confirmação de sua parte. No entanto, nosso time comercial ainda entrará em contato com você para negociar valores, acertar os detalhes finais e formalizar o pedido comercial.

### Template ticket script:
!!! info  "Dica"
    Você pode acessar o template ticket script diretamente pela macro `Escalonar TI(Script db2)` disponivel nas macros do zendesk

>1 - É possível realizar o processo diretamente pelo sistema? (Campo Obrigatório)   
Sim → Informar passo a passo que foi orientado ao cliente (menu, telas, parâmetros).    
Não → Informar claramente por que não é possível realizar pelo sistema padrão.  

>2 - Descrição detalhada da solicitação de Script (Campo Obrigatório):  
(Detalhar: O que deve ser ajustado / Quais tabelas / processos / movimentações / período / detalhar exatamente o que o script deve ajustar.)

>3 - Causa da demanda (Campo Obrigatório):  
(Detalhar: Origem do problema/Erro de sistema/Falha de versão/Problema de OFF/Processo operacional)

>4 - Solução esperada: 
(Regras obrigatórias / Validação esperada / Resultado esperado) 
Observação: Caso tenha, anexar arquivos relevantes como, planilhas, arquivos PDF, vídeos, prints, consultas que foram utilizadas para validar dados, etc.

## Tentativas de contato
### 2ª Tentativa:
>Bom dia! Tudo bem?  
Gostaria de validar o ticket (Link ou numero do ticket).    
Esta é a **segunda tentativa de contato** para desenvolvimento. Lembrando que realizamos **três tentativas**, e se não houver retorno, seu ticket será **cancelado ao final do dia da terceira tentativa** (Segunda-feira - xx/xx/xxxx).

### 3ª Tentativa(manhã):
>Bom dia! Tudo bem?     
Gostaria de validar o ticket (Link ou numero do ticket).    
Hoje é meu **terceiro contato** para validação da demanda solicitada. Caso não haja um retorno efetivo, o ticket será **cancelado ao final do dia de hoje**.

### 3ª Tentativa(tarde):
>Boa tarde!     
Seu ticket (Link ou numero do ticket) está sendo **cancelado por falta de retorno**.    
Caso ainda deseje que a solicitação documentada seja desenvolvida por nossa equipe, pedimos que entre em contato pelo **Chat**, onde um analista poderá abrir um **novo ticket**.   
Bom trabalho e até mais! 🤝