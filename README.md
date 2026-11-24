# Margaridas em ASCII

Um buquê de margaridas animado, desenhado com caracteres ASCII, que cresce na tela, desabrocha e fica sob um céu de estrelas.

- Os caules crescem, surgem os botões e as margaridas abrem girando
- Laço rosa amarrando o buquê
- Estrelas piscando no fundo; a cada 4 segundos uma delas brilha mais forte
- Toque/clique na tela para replantar
- Renderização em WebGL (com reserva em Canvas 2D), fluida até em telas de 120 Hz
- Feito para funcionar bem no celular

## Rodando

Com Docker:

```bash
docker compose up -d --build
```

Abra http://localhost:8085.

Sem Docker, basta abrir o `index.html` no navegador.

### Link público temporário

Para gerar um link `https://xxxx.trycloudflare.com` e compartilhar:

```bash
docker compose --profile share up -d
docker logs margaridas-tunnel 2>&1 | grep trycloudflare.com
```

O link funciona enquanto os contêineres estiverem rodando.

## Personalizando

Parâmetros na URL:

| Parâmetro | Efeito | Exemplo |
|-----------|--------|---------|
| `para` | Nome no título ("Margaridas pra *Nome*") | `?para=Margarida` |
| `msg` | Troca o título inteiro | `?msg=Feliz%20aniversário` |
| `sub` | Troca a linha pequena abaixo do título | `?sub=com%20amor` |
| `2d` | Força o modo Canvas 2D | `?2d` |
| `t` | Pula a animação para N segundos (teste) | `?t=14` |

## Estrutura

- `index.html` — página completa (HTML, CSS e JS, sem dependências)
- `Dockerfile` — imagem nginx servindo a página
- `docker-compose.yml` — serviço web na porta 8085 e túnel opcional
