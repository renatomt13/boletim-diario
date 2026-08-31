# Boletim Diário

Arquivo histórico e dashboard do boletim diário de tecnologia e mercado de trabalho (Brasil e global).

## Estrutura

- `boletim-diario-config.md` — configuração de escopo, fontes e formato do boletim.
- `data/` — um arquivo JSON por dia (`AAAA-MM-DD.json`) com as 10 notícias daquela edição.
- `dashboard.html` — cópia de referência do dashboard interativo (cards com tags), publicado ao vivo como Claude Artifact.

## Dashboard ao vivo

O dashboard interativo ("Boletim Radar") é publicado e atualizado automaticamente todos os dias às 10h (horário de São Paulo):

https://claude.ai/code/artifact/d438b72f-f6a0-4434-95e5-b0e7b3bd4d0a

## Automação

Uma rotina agendada (Claude Code) roda diariamente:
1. Busca notícias reais do dia nas fontes configuradas.
2. Salva o arquivo `data/AAAA-MM-DD.json` neste repositório com as 10 notícias.
3. Atualiza o dashboard ao vivo com as notícias do dia.

## Formato de `data/AAAA-MM-DD.json`

```json
{
  "date": "2026-08-31",
  "items": [
    {
      "source": "TechCrunch",
      "region": "GL",
      "cats": ["IA", "Tecnologia"],
      "title": "...",
      "summary": "...",
      "url": "https://..."
    }
  ]
}
```

`region` é `"BR"` ou `"GL"`. `cats` usa somente: `IA`, `Tecnologia`, `Startups`, `Dados`, `Mercado de Trabalho`. `url` é `null` quando não há uma URL confirmada da matéria original.
