# Política de segurança das atualizações do DarkClean

Este repositório distribui binários Windows. A segurança depende de **assinar os arquivos de atualização antes de publicá-los**.

## Regras de confiança

- O cliente fixa uma chave pública Ed25519 e o thumbprint do certificado Authenticode do editor na compilação.
- O manifesto é verificado **antes** de processar seus dados de instalação.
- O hash SHA-256 e o tamanho de cada pacote devem coincidir com o manifesto assinado.
- Pacotes são instalados em diretório de versão separado; a versão anterior deve ser preservada.
- Versões beta/draft e downgrades não são instalados automaticamente.
- Nunca executar scripts remotos ou atualizações sem assinatura válida.

## Proteção das chaves

A chave **privada** Ed25519 deve ser gerada e armazenada somente no computador do publicador (preferencialmente em dispositivo seguro ou cofre de segredos apropriado). Nunca incluir a chave privada ou sua senha no repositório, arquivos ZIP, instaladores ou conversas.

A assinatura Authenticode exige um certificado de publicação de código válido, cuja chave privada também deve ser protegida. Um certificado de teste não substitui uma assinatura confiável para distribuição pública.

## Relatos de vulnerabilidades

Evite divulgar publicamente detalhes exploráveis antes de a correção estar pronta. Entre em contato com o mantenedor do repositório por um canal privado disponibilizado por ele.

## Estado

A preparação da V10 não equivale a uma release auditada. Não considerar o mecanismo pronto para distribuição pública sem os testes completos em Windows, assinatura e validação de rollback.
