# DetailOS PWA — MVP 0.1

Protótipo funcional, **não pronto para dados reais de clientes**.

## Executar

Requer Python 3. Na pasta do projeto:

```bash
python3 -m http.server 8080
```

Acesse `http://localhost:8080` no computador. Para instalar o PWA no celular, publique em hospedagem HTTPS (ex.: Vercel/Netlify). A câmera e o service worker dependem de HTTPS ou localhost. No celular, use o menu do navegador **Adicionar à tela inicial**.

## Recursos

- Cadastro de clientes e veículos.
- Ordens de serviço SD-01, SM-01 e SE-01.
- Roteiro de evidências antes/depois, por região.
- Checklist de qualidade e bloqueio de conclusão.
- Relatório HTML imprimível / Salvar como PDF.
- Compartilhamento do PDF manualmente pelo WhatsApp.
- Histórico de atendimentos no navegador.
- Instalação PWA e cache básico dos arquivos da interface.

## Limitações críticas

- Dados e fotos são armazenados no IndexedDB **do navegador/dispositivo**, sem autenticação, backup, criptografia de aplicação ou sincronização.
- O cache offline cobre a interface, **não** implementa fila de sincronização de fotos.
- O relatório é gerado pelo navegador via impressão (`Salvar como PDF`), não como PDF de servidor.
- Não há cobrança, contratos, calendário recorrente ou envio automático via WhatsApp.
- Não use dados pessoais reais ou fotos de clientes antes de implantar segurança, consentimento, backups e políticas de retenção.
- Limpar dados do navegador pode apagar todos os registros. Navegação privada pode não persistir.

## Próximas etapas de produção

Supabase Auth, PostgreSQL, Storage privado, políticas RLS, papéis operador/gestor, sincronização offline, relatórios PDF gerados no servidor, agenda recorrente, financeiro e auditoria.

## Correção 0.2
- Observações digitadas são salvas automaticamente ao clicar em Visualizar relatório / PDF.
- Observações aparecem no PDF com quebras de linha preservadas.
- Título atualizado para Checklist de Qualidade.
- Para atualizar, substitua os arquivos na mesma pasta e recarregue a página. Os dados do navegador são preservados desde que a origem (localhost:8080) e o perfil do navegador permaneçam iguais.


## Atualização DET-004 (OS sequencial)
- Ordens novas recebem número 00001, 00002, etc.
- Ordens antigas recebem número ao abrir o aplicativo atualizado, em ordem de criação.
- Número aparece na lista, na tela do atendimento e no cabeçalho do PDF.
- O identificador técnico interno permanece inalterado.
- A numeração é local ao navegador e não é segura para múltiplos operadores/dispositivos; antes de produção, usar contador transacional no servidor.
