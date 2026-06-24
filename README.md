# 🏆 Bolão da Família Dias

Aplicação web para gerenciar o bolão de futebol da família, com foco nos jogos da Seleção Brasileira. Permite registrar palpites de placar, controlar pagamentos e exibir um ranking de acertos em tempo real.

## Como funciona

Cada participante aposta em um placar exato para um jogo do Brasil. Ao encerrar o jogo com o resultado final, o sistema calcula automaticamente quem acertou. O prêmio é o total arrecadado nas apostas daquele jogo — dividido igualmente se houver mais de um vencedor. Se ninguém acertar, o valor vai pro lanche do Lennon.

## Funcionalidades

- **Jogos** — lista todos os jogos cadastrados com estatísticas por jogo (total de apostas, valor arrecadado, valor já pago)
- **Apostas** — cada jogo aceita múltiplos palpites de placar com valor em reais e controle de pagamento
- **Encerramento** — inserção do placar final com cálculo automático de vencedores e divisão do prêmio
- **Ranking** — placar geral de acertos por participante em todos os jogos já encerrados (medalhas ouro/prata/bronze)
- **Usuários** — cadastro de participantes recorrentes com autocomplete no campo de nome ao adicionar apostas

## Tecnologia

| Camada | Tecnologia |
|---|---|
| Frontend | HTML + CSS + JavaScript puro (sem framework) |
| Backend | [Supabase](https://supabase.com) (PostgreSQL gerenciado) |
| Deploy | Qualquer servidor estático ou GitHub Pages |

Toda a aplicação vive em **um único arquivo HTML** (`index (4).html`). Não há build, bundler ou dependências locais.

## Estrutura do banco de dados (Supabase)

Tabela: `bolao_dias`

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | integer | Chave primária (sempre `1`) |
| `games` | jsonb | Array de jogos com apostas embutidas |
| `usuarios` | jsonb | Lista de participantes cadastrados |
| `updated_at` | timestamptz | Data da última atualização |

Todos os dados ficam em uma única linha com `id = 1`.

## Configuração

1. Crie um projeto no [Supabase](https://supabase.com) e crie a tabela `bolao_dias` com as colunas acima
2. Insira uma linha inicial: `INSERT INTO bolao_dias (id, games, usuarios) VALUES (1, '[]', '[]')`
3. No arquivo HTML, atualize as variáveis:
   ```js
   const SUPABASE_URL = 'sua-url-aqui';
   const SUPABASE_ANON_KEY = 'sua-chave-aqui';
   ```
4. Abra o arquivo no navegador ou faça deploy em qualquer hospedagem estática

## Pagamentos

A chave PIX exibida no topo da aplicação é `(62) 982390172`. Para alterar, edite a linha correspondente no HTML:

```html
💰 Chave pix para pagamento: <strong>(62) 982390172</strong>
```

## Regras do bolão

- O acerto é por **placar exato** (ex: Brasil 2 x 1 Argentina)
- O prêmio de cada jogo é a soma de todas as apostas daquele jogo
- Múltiplos vencedores dividem o prêmio igualmente
- Nenhum acerto = valor fica para o organizador (lanche do Lennon 🥪)
