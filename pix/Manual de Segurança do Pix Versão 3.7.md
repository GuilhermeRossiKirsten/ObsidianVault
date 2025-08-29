### 1. **Condições preliminares**

Antes de tudo, sua instituição precisa:

- Ser **participante do Pix** (ou integrar via um PSP autorizado).
- Ter acesso à **RSFN (Rede do Sistema Financeiro Nacional)**.
- Obter e ativar os **certificados digitais ICP-Brasil** necessários.

---

### 2. **Segurança na comunicação**

- A comunicação com as APIs do Pix deve usar:
    
    - **HTTP/1.1**
    - **TLS 1.2 ou superior**
    - **Autenticação mútua (mTLS)** com certificado padrão SPB.
    - Cipher Suite mínima obrigatória: `ECDHE-RSA-AES-128-GCM-SHA256`.

---

### 3. **Assinatura digital das mensagens**

- Toda transação deve ser assinada digitalmente.
    
- Padrão adotado:
    
    - **SPI (Sistema de Pagamentos Instantâneos):** XMLDSig (padrão ISO 20022).
    - **DICT (Diretório de Identificadores de Contas Transacionais):** XMLDSig fora do padrão ISO.
- O processo inclui:

	- Obter mensagem assinada
	- Construir o `<KeyInfo>`
	- Extrair `BAH` (tag `<AppHdr>`)
	- Extrair mensagem iso 20.022 (tag `<Document>`)
    - (`SignedInfo`) definir algoritmo de interno de canonicalização (`xml-exc-c14n#`)
    - Assinatura com **RSA-SHA256**
    - Validação da estrutura `<Signature>`, `<KeyInfo>`, e digestos SHA-256 codificados em base64.

---

### 4. **QR Code Dinâmico**

- Usado para iniciar pagamentos.
- Contém uma **URL criptografada** que leva a um **JWS** (JSON Web Signature).
- Requisitos:
    - HTTPS (TLS 1.2 ou superior).
    - Certificado SSL EV válido, sem wildcard, com CN ou SAN correspondente ao domínio.
    - `pixUrlAccessToken` com **mínimo de 120 bits de entropia**.
    - Assinatura digital do payload em JWS utilizando `PS256`, `RS256` ou `ES256`.

---

### 5. **Certificados digitais**

Tipos necessários:

- **CERTPIC** – autenticação da conexão SPI.
- **CERTPIA** – assinatura digital de mensagens SPI.
- **CERTQRC** – certificado para sites que hospedam QR Codes.

**Ativação via STA** (Sistema de Transferência de Arquivos):

- Envio no formato **PEM**, sem cadeia nem chave privada.
- Processamento e validação pelo BC em até **7 dias** úteis.
- A versão de produção e homologação utilizam caminhos diferentes.

---

### 6. **Implementação segura de sistemas e APIs**

- Todas as APIs devem:
    
    - Usar mTLS.
    - Implementar validação de certificado.
    - Proteger contra engenharia reversa (apps mobile).
    - Ter controle de acesso e autenticação robusta.
- Segurança **majoritariamente no backend**.
    

---

### 7. **Logs e auditoria**

- Devem ser registrados:
    - Acessos ao SPI e DICT.
    - Erros e transações.
    - Assinaturas e JWS processados.
- Retenção mínima definida para cada tipo de dado.

---

### 8. **Gestão de ciclo de vida de certificados**

- **Revogação automática**: 24h antes do vencimento.
- Desativação manual:
    - Modalidade programada ou por incidente de segurança.
    - Via **BC Correio** e confirmação com a Central de Atendimento Pix.
- Verificação de revogação ocorre **offline**, via análise periódica das LCRs (Listas de Certificados Revogados).
    

---

###  Resumo do fluxo

1. **Ingressar no Pix** → credenciamento/autorização.
2. **Gerar e ativar certificados** → via STA.
3. **Implementar APIs seguras** → TLS, autenticação mútua, assinatura.
4. **Iniciar pagamentos (QR Codes)** → URLs protegidas e assinaturas JWS.
5. **Verificar e validar tudo** → certificados, cadeias, assinaturas.
6. **Manter logs e dados** → para rastreabilidade e conformidade.