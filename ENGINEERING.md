# Decisões e aprendizados de engenharia

## 1. Persistência local como proteção, servidor como confirmação

**Problema:** conectividade e ciclo de vida do iOS não são contínuos. Uma caminhada não pode depender apenas da memória do processo.

**Abordagem:** preservar dados locais da atividade, checkpoints e registro incremental; separar o salvamento do percurso da confirmação das regras do jogo no servidor.

**Trade-off:** recuperação e sincronização ficam mais complexas. É necessário distinguir atividade ativa, encerrada, pendente e validada e testar interrupções em cada etapa.

**Limite:** nenhum mecanismo de checkpoint reconstrói pontos GPS que nunca foram coletados. Encerramento forçado e permissões do sistema impõem limites reais.

## 2. Reenvios idempotentes e transações atômicas

**Problema:** uma falha de resposta não prova que o servidor deixou de processar a operação.

**Abordagem:** identificar operações e transações, rejeitar reutilização por outra conta e aplicar créditos de forma atômica. Exercitar repetição, propriedade incorreta e rejeições com rollback em testes SQL.

**Trade-off:** o estado de processamento e a vinculação precisam ser preservados mesmo quando o app não recebeu a confirmação.

## 3. Sessão e isolamento entre contas

**Problema:** exclusão, logout e entrada como convidado podem deixar estado visual ou local associado à sessão anterior.

**Abordagem:** armazenamento por conta, políticas explícitas de acesso ao progresso e invalidação de operações antigas ao mudar a identidade. Testar exclusão → login → convidado → reabertura.

**Aprendizado:** apagar uma foto não é concluir uma exclusão. A navegação, a sessão e os dados associados também precisam ser verificados.

## 4. Compra confirmada não é funcionalidade liberada automaticamente

**Problema:** Apple, backend comercial e políticas que controlam as funcionalidades são etapas distintas.

**Abordagem:** validar provas, vincular o benefício à conta e integrar o acesso tanto às informações de território quanto à aparência pública. Verificar o resultado a partir de outro aparelho.

**Aprendizado:** testar apenas a mensagem de sucesso do pagamento deixa uma lacuna entre confirmação comercial e experiência real.

## 5. Renderização e energia

**Problema:** mapa, efeitos visuais e atualizações de dados podem continuar consumindo recursos atrás de um menu.

**Abordagem:** controlar o trabalho de apresentação conforme a visibilidade da tela, sem interromper a coleta de uma atividade ativa.

**Limite:** redução de trabalho não permite afirmar que um aparelho nunca vai aquecer. Perfil de energia, sessões longas e comparação em aparelhos físicos continuam necessários.

## 6. Distribuição e revisão

A experiência inclui build, archive, distribuição pelo TestFlight, testes com familiares e preparação dos metadados da App Store. Um bloqueio automatizado por ausência do link da EULA na descrição foi corrigido nos metadados e reenviado sem alteração do binário.

A revisão da loja faz parte da entrega do produto. Submissão não equivale a aprovação, e aprovação não substitui testes de qualidade.

## Próximos passos

- Ampliar testes de GPS e recuperação em diferentes modelos de iPhone.
- Medir consumo e comportamento térmico com cenários repetíveis.
- Acompanhar compras, renovações e restaurações em condições reais de distribuição.
- Aprimorar mensagens de estados pendentes e de expiração de assinaturas.

Esses itens são objetivos de evolução, não garantias de funcionalidades já concluídas.
