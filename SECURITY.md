# Política de Segurança

## Versões Suportadas

| Versão | Suportada          |
| ------ | ------------------ |
| latest | :white_check_mark: |

## Reportando uma Vulnerabilidade

Se você descobrir uma vulnerabilidade de segurança em qualquer repositório da organização **tekojs**, **não** abra uma issue pública. Em vez disso, siga as instruções abaixo:

1. **Envie um e-mail** para [security@tekojs.org](mailto:security@tekojs.org) descrevendo o problema com o máximo de detalhes possível.
2. **Inclua** no seu relatório:
   - Descrição detalhada da vulnerabilidade
   - Passos para reproduzir o problema
   - Impacto potencial
   - Versão afetada (se aplicável)
3. **Aguarde** o contato da equipe em até **7 dias úteis**.

## Segredos e Credenciais

- Nunca commite segredos, tokens, senhas ou credenciais em nenhum repositório.
- Utilize as [GitHub Actions Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets) para armazenar informações sensíveis em pipelines de CI/CD.
- Caso um segredo seja acidentalmente exposto, **revogue-o imediatamente** e notifique a equipe.
- Utilize ferramentas como [git-secrets](https://github.com/awslabs/git-secrets) ou [truffleHog](https://github.com/trufflesecurity/trufflehog) para prevenir vazamentos.

## Controles de Acesso

- O princípio do menor privilégio deve ser aplicado a todos os colaboradores e integrações.
- Revise periodicamente as permissões de colaboradores e aplicações conectadas à organização.
- Ative a autenticação de dois fatores (2FA) obrigatória para todos os membros da organização.

## Comunicação Responsável

Agradecemos a divulgação responsável de vulnerabilidades. Reconheceremos sua contribuição assim que o problema for corrigido.
