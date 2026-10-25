# Laboratório de Cibersegurança

## Objetivo

Documentar atividades práticas de reconhecimento, enumeração de
serviços e validação controlada de autenticação em um ambiente
educacional isolado.

## Ambiente

- Máquina de testes: Kali Linux
- Máquina-alvo: Metasploitable 2
- IP do alvo no laboratório: `192.168.56.102`
- Ferramentas: Nmap, Medusa e smbclient
- Escopo: máquinas próprias e rede virtual autorizada

## Atividades realizadas

### Reconhecimento de serviços

Foram identificados serviços FTP, HTTP e SMB no alvo. Os detalhes
observados estão registrados nos arquivos de evidência.

### FTP

- Verificação de acesso anônimo.
- Enumeração do serviço.
- Teste controlado de uma combinação de credenciais com Medusa.

### HTTP

- Enumeração do serviço web.
- Registro de observações sobre a aplicação DVWA.
- Testes manuais documentados separadamente.

### SMB

- Reconhecimento das portas 139 e 445.
- Enumeração de compartilhamentos.
- Verificação de listagem anônima e autenticada.
- Teste controlado de uma combinação de credenciais com Medusa.
- Registro das listagens dos compartilhamentos `tmp`, `opt` e
  `msfadmin`.

## Principais observações

- O serviço FTP permitiu acesso anônimo no ambiente testado.
- O teste controlado de FTP com Medusa identificou uma combinação
  de credenciais aceita pelo serviço.
- O teste SMB com Medusa reportou autenticação bem-sucedida e
  acesso permitido ao recurso `ADMIN$`.
- Foi possível listar determinados compartilhamentos SMB.
- Os resultados são específicos do ambiente e das permissões
  observadas; não comprovam, isoladamente, controle administrativo
  completo do sistema operacional.

## Evidências

Os resultados detalhados estão na pasta [`evidencias/`](evidencias/).

Arquivos de referência:

- `servicos.txt`
- `ftp-enumeracao.txt`
- `ftp-diagnostico.txt`
- `ftp-listagem.txt`
- `http-enumeracao.txt`
- `smb-enumeracao.txt`
- `smb-compartilhamentos.txt`
- `smb-shares-nmap.txt`
- `medusa-versao.txt`
- `medusa-modulos.txt`
- `medusa-ftp-teste.txt`
- `medusa-smb-reconhecimento.txt`
- `medusa-smb-opcoes.txt`
- `medusa-smb-teste.txt`
- `medusa-smb-anonimo.txt`
- `medusa-smb-tmp-listagem.txt`
- `medusa-smb-tmp-autenticado.txt`
- `medusa-smb-opt-listagem.txt`
- `medusa-smb-msfadmin-listagem.txt`
- `medusa-relatorio.txt`
- `dvwa-bruteforce.txt`

## Recomendações defensivas

- Desabilitar acesso anônimo a serviços quando não for necessário.
- Substituir credenciais padrão e adotar senhas fortes e exclusivas.
- Restringir o acesso a SMB às máquinas e redes autorizadas.
- Revisar permissões de compartilhamentos e arquivos.
- Atualizar ou desativar serviços vulneráveis.
- Monitorar tentativas de autenticação e manter registros de auditoria.

## Limitações

Este trabalho é um exercício educacional, não uma auditoria completa
ou certificação de segurança. As verificações de listagem não
comprovam acesso de leitura ou escrita a todos os arquivos.
Nenhum resultado deve ser generalizado para sistemas diferentes
do ambiente testado.

## Segurança e autorização

Todas as atividades devem ocorrer apenas em sistemas próprios ou
com autorização explícita. O arquivo local `senhas-lab.txt` contém
dados de laboratório e está excluído do controle de versão pelo
`.gitignore`; ele não deve ser publicado.
