# DarkClean — Publicação de versões oficiais

Este repositório público hospeda **somente os releases e os documentos de atualização do DarkClean**. O código-fonte pode continuar em um repositório privado.

## Formato dos releases

Tags estáveis: `v10.0.0`, `v10.1.0`, `v10.1.1`, seguindo SemVer.

Para cada atualização **após a instalação inicial V10**, publique juntos:

- `DarkClean-Package-v10.1.0.zip` — executável Windows e recursos da versão.
- `manifest.json` — versão, tamanho do arquivo e hash SHA-256.
- `manifest.sig` — assinatura Ed25519 **sobre os bytes exatos** do manifesto.

A primeira instalação exige um instalador Windows separado `DarkClean-Setup-v10.0.0.exe`, gerado com Inno Setup e assinado digitalmente antes da distribuição.

## Processo seguro de publicação

1. Compile os três executáveis da V10 em Windows: app, launcher e atualizador.
2. Assine os executáveis com certificado de publicação de código.
3. Gere o instalador inicial com Inno Setup e assine o instalador.
4. Teste em Windows 10/11, inclusive o LibreHardwareMonitor e a recuperação.
5. Para cada atualização, crie o pacote ZIP **depois** de assinar o `DarkClean.exe`.
6. Gere `manifest.json` e `manifest.sig` com a chave de assinatura local do publicador.
7. Confira nomes, tag, SHA-256, arquivo e assinatura; publique um Release estável apenas após testes.
8. Ative Immutable Releases nas configurações do repositório quando disponível.

### Verificação das versões

O aplicativo consulta:
`https://api.github.com/repos/zDaark333/DarkClean-Updates/releases/latest`

A publicação no GitHub, sozinha, **não autoriza uma instalação**. O atualizador exige chave pública incorporada ao executável, assinatura Ed25519 do manifesto, hash SHA-256 e certificado Authenticode do editor correspondente ao esperado.

### Atenção

- Não envie arquivos `.pem`, senhas, tokens, nem outras chaves privadas.
- Nunca publique executáveis de teste como release oficial.
- Modificações no próprio launcher/atualizador exigem um **instalador completo** assinado.
- A V9 e anteriores não possuem o lançador gerenciado e necessitam instalar a V10 uma vez.
- Atualmente o repositório pode não conter nenhum release; isso é normal durante a preparação.
