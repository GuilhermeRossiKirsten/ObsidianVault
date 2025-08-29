---
tags:
  - TDD
---

# Tipos de testes
## Teste de Unidade / "Unitários"

 Os testes unitários focam em verificar o comportamento de pequenas unidades de código, como funções, métodos ou classes. Eles são escritos para testar uma funcionalidade específica de forma isolada, sem dependências externas.


- Isolamento de Erros: Ao testar componentes individualmente, fica mais fácil identificar o erro
- Documentação Viva: Os testes unitários servem como forma de documentação que demonstra como cada unidade deve se comportar
- Facilidade de Refatoração: Com testes unitários abrangentes, desenvolvedores podem refatorar o código com confiança, sabendo que os testes irão alertá-los sobre possíveis quebras
- Contratos de interface: Garantem que as entradas e saídas das funções permanecem consistentes prevenindo impactos em partes do código que dependem delas.

## Teste de Integração

Os testes de integração verificam a interação entre diferentes módulos ou componentes do sistema. O objetivo é assegurar que, quando combinamos, esses componentes funcionem harmoniosamente.

- Detecção de Problemas de Compatibilidade: Identifica incompatibilidades entre diferentes partes do sistema ou com serviços externos.
- Validação de Fluxos de Dados: Garante que os dados fluem corretamente através dos diferentes componentes.
- Dependências Externas: Auxilia a identificar falhas na integração com bancos de dados, sistemas de arquivos ou serviços de terceiros
- Erros de comunicação: Captura problemas na troca de informações entre módulos, como chamadas de API malformadas ou contratos quebrados.

## Testes End-to-End (E2E)

Os testes E2E simulam o comportamento real do usuário, testando o sistema completo desde a interface até o backend e vice-versa. Eles verificam se todos os componentes funcionam juntos em um ambiente que replica o de produção

- Experiência de Usuário: Assegura que o software atende às expectativas do usuário final
- Validação de fluxo críticos: Confirma que o processos essenciais, como cadastro, login ou compras, funcionam sem problemas.
- Ambiente Realista: Testa o sistema em condições próximas ao uso real, incluindo possíveis interações complexas.
- Erros de integrações Completa: Identifica problemas que só surgem quando todos os componentes estão operando juntos
- Ambiguidade nos requisitos: Ajuda a revelar inconsistências ou mal-entendidos nos requisitos do sistema



# Test driven development
