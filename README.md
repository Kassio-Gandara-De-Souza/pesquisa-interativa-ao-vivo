# Pesquisa interativa ao vivo

Sistema de pesquisa em tempo real usado em um encontro nacional de uma rede de atendimento institucional: os participantes respondem pelo celular e os resultados aparecem ao vivo no telão do evento.

> Desenvolvido por mim durante o estágio (outubro de 2026).
> Este repositório é uma **vitrine**: o código, os dados dos participantes, o questionário e as informações internas da instituição não são publicados.

## O problema

Em um encontro com cerca de 150 pessoas de vários estados, a organização precisava coletar a opinião de todos durante o evento e discutir os resultados na hora, sem esperar a tabulação de um formulário comum.

## O que o sistema faz

- **Formulário mobile-first**, acessado por QR Code, com o questionário do evento.
- **Telão ao vivo** com gráficos que se atualizam a cada resposta, ranking das opções e um mural com as respostas abertas.
- **Uma resposta por aparelho**, com controle por sessão.
- **Exportação em CSV** para a análise depois do evento.
- Identidade visual seguindo o padrão institucional.

## Arquitetura

```
Celular do participante ── formulário (Next.js)
                                │ grava
                                ▼
                      Supabase (Postgres + Realtime)
                                │ envia cada resposta em tempo real
                                ▼
                 Telão /tv ── gráficos, ranking, mural, QR Code
```

## O que eu fiz

- Defini a arquitetura e o **esquema do banco** antes de começar o código.
- Construí o formulário, o telão e a exportação em CSV.
- Usei o **Supabase Realtime** para o telão atualizar sem recarregar, com reconexão para não perder respostas em uma rede de evento instável.
- Fiz os testes antes do evento, incluindo quedas de rede propositais para validar que os números do telão voltavam a bater com o banco.
- Usei ferramentas de IA como apoio para acelerar partes do desenvolvimento e das revisões; o planejamento, as decisões técnicas, os testes e a validação final foram meus.

## Resultado

Usado ao vivo no evento, com cerca de 150 participantes respondendo ao mesmo tempo.

## Tecnologias

Next.js · React · Supabase (Postgres, Realtime) · Recharts · Framer Motion · Vercel

## Contato

Kassio Gândara de Souza · [LinkedIn](https://www.linkedin.com/in/kassiogandara) · [Portfólio](https://kassio-souza.vercel.app)
