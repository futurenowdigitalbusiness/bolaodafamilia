# 🏆 Bolão da Família Dias

Uma aplicação web moderna e responsiva para gerenciar apostas em jogos da seleção brasileira de futebol entre familiares e amigos.

## 📋 Sobre o Projeto

**Bolão da Família Dias** é uma plataforma interativa que facilita a organização de "bolões" (piscinas de apostas) em jogos de futebol. Permite criar jogos, adicionar apostas com palpites, controlar pagamentos e gerar um ranking dos participantes mais acertadores.

A aplicação é ideal para grupos familiares e de amigos que desejam acompanhar jogos da Seleção Brasileira de forma divertida, com um sistema de prêmios baseado em quem acerta o placar exato.

## ✨ Principais Funcionalidades

### 🎮 Gestão de Jogos
- **Criar novos jogos**: Adicione jogos do Brasil especificando adversário, data e fase da competição
- **Visualizar jogos**: Veja todos os jogos cadastrados com status (pendente/encerrado)
- **Encerrar jogo**: Insira o placar final e calcule automaticamente os acertadores
- **Reabrir jogo**: Edite o resultado de um jogo já encerrado
- **Remover jogo**: Delete um jogo e todas as suas apostas associadas

### 💰 Gestão de Apostas
- **Adicionar apostas**: Participantes adicionam seus palpites com valor apostado
- **Palpite exato**: Simples (gols do Brasil x gols do adversário)
- **Controle de pagamento**: Marque apostas como pagas ou pendentes
- **Remover aposta**: Delete uma aposta individual se necessário

### 🏅 Ranking
- **Ranking geral**: Visualize o desempenho de todos os participantes
- **Cálculo de acertos**: Estatística automática de acertos vs total de apostas
- **Medalhas**: Prêmios visuais para 1º, 2º e 3º colocados 🥇 🥈 🥉

### 📊 Estatísticas por Jogo
- Número de apostas
- Total apostado
- Total pago

### 💬 Notificações Interativas
- Mensagens de sucesso (toast notifications)
- Modais personalizados com emojis para:
  - Aposta confirmada
  - Acertos (um ou múltiplos)
  - Nenhum acerto ("para o lanche do Lennon")

## 🎨 Design & UX

- **Interface moderna**: Dark mode com cores vibrantes
- **Totalmente responsivo**: Funciona perfeitamente em desktop, tablet e smartphone
- **Tema escuro**: Reduz fadiga ocular
- **Código limpo**: HTML/CSS/JS puro, sem dependências pesadas

## 🛠 Tecnologias

- **Frontend**: HTML5, CSS3, JavaScript vanilla
- **Backend**: Supabase (banco de dados em tempo real)
- **Armazenamento**: JSON estruturado no Supabase
- **UI Components**: Modals, tabs, tabelas, inputs customizados

## 🚀 Como Usar

### 1️⃣ Criar um Jogo
1. Clique na aba **"+ Novo jogo"**
2. Preencha:
   - **Adversário**: Qual seleção vai jogar contra o Brasil
   - **Data**: Quando o jogo acontece
   - **Fase**: Grupo A, Oitavas, Final, etc.
3. Clique em **"Criar jogo"**

### 2️⃣ Adicionar Apostas
1. Na aba **"Jogos"**, localize o jogo desejado
2. Preencha a seção "Adicionar aposta":
   - **Nome**: Quem está apostando
   - **Gols Brasil**: Quantos gols você acha que o Brasil vai marcar
   - **Gols adversário**: Quantos gols você acha que o adversário vai marcar
   - **Valor (R$)**: Quanto você está apostando
3. Clique em **"Adicionar aposta"**

### 3️⃣ Encerrar um Jogo
1. Localize o jogo já finalizado
2. Na seção "Encerrar jogo / inserir resultado final":
   - Preencha os gols do Brasil
   - Preencha os gols do adversário
3. Clique em **"Encerrar e calcular acertos"**
4. O sistema identificará automaticamente quem acertou o placar exato

### 4️⃣ Acompanhar Pagamentos
1. Clique na coluna **"Pago"** de qualquer aposta para marcar como pago/pendente
2. As estatísticas se atualizam automaticamente

### 5️⃣ Ver Ranking
1. Clique na aba **"Ranking"**
2. Veja quem mais acertou (acertos/total de apostas)

## 💳 Informações de Pagamento

- **Chave PIX**: (62) 982390172
- Os valores das apostas são consolidados por jogo
- O prêmio é dividido entre os acertadores do placar exato

## 📱 Responsividade

| Dispositivo | Suporte |
|---|---|
| Desktop | ✅ Totalmente otimizado |
| Tablet | ✅ Layout adaptado |
| Mobile | ✅ Totalmente responsivo |
| Pequenas telas | ✅ Otimizado para < 520px |

## 🗂 Estrutura de Dados

### Jogo
```javascript
{
  id: "g[timestamp][random]",           // ID único
  adversario: "Argentina",               // Nome do adversário
  data: "2024-06-15",                   // Data no formato YYYY-MM-DD
  fase: "Oitavas de final",             // Fase da competição
  status: "pendente" | "encerrado",     // Status do jogo
  placarBrasil: 2,                      // Gols do Brasil (null se pendente)
  placarAdversario: 1,                  // Gols do adversário (null se pendente)
  apostas: [...]                         // Array de apostas
}
```

### Aposta
```javascript
{
  id: "b[timestamp][random]",           // ID único
  nome: "João Silva",                   // Nome do apostador
  golBR: 2,                             // Gols do Brasil (palpite)
  golADV: 1,                            // Gols do adversário (palpite)
  valor: 50.00,                         // Valor apostado
  pago: false                           // Status de pagamento
}
```

## ⚙️ Configuração

### Supabase
A aplicação utiliza Supabase como backend. Certifique-se de:

1. Ter uma conta no [Supabase](https://supabase.com)
2. Criar uma tabela chamada `bolao_dias` com estrutura JSON para armazenar os dados
3. Substituir `SUPABASE_URL` e `SUPABASE_ANON_KEY` no código

## 🎯 Casos de Uso

- 👨‍👩‍👧‍👦 Famílias que gostam de acompanhar futebol
- 🏢 Grupos de amigos e colegas de trabalho
- 🏠 Reuniões sociais durante Copa do Mundo ou outras competições
- 💬 Whatsapp groups com apostas

## 💡 Dicas

- Use a funcionalidade "Reabrir jogo" se precisar corrigir um resultado inserido errado
- O ranking só conta jogos encerrados
- Sempre confirme os pagamentos para não perder o controle financeiro
- O prêmio é acumulativo por jogo (quanto maior o número de apostadores, maior o prêmio)

## 📝 Notas

- Todos os dados são salvos em tempo real no Supabase
- A aplicação é completamente cliente-side (roda no navegador)
- Suporta múltiplos usuários acessando simultaneamente

## 🔒 Privacidade & Segurança

- Os dados são armazenados no Supabase com permissões de acesso anônimo
- Não há autenticação obrigatória (ideal para grupos fechados)
- Todos que acessam o link podem gerenciar os dados
- Recomenda-se usar em um ambiente privado/controlado

## 🐛 Troubleshooting

### "Erro: não foi possível conectar ao Supabase"
- Verifique sua conexão com a internet
- Confirme que a URL e chave do Supabase estão corretas
- Verifique se a tabela existe no banco de dados

### Dados não salvam
- Confirme que há conexão com a internet
- Verifique as permissões do banco de dados no Supabase
- Atualize a página

### Aplicação lenta
- Isso pode ocorrer se houver muitos jogos/apostas
- Considere arquivar jogos antigos em uma tabela separada

## 📞 Suporte

Para dúvidas ou problemas, entre em contato com o administrador do grupo.

---

**Desenvolvido para a Família Dias** 🇧🇷⚽

*Que o melhor acertador ganhe! 🏆*
