# 🔮 Oráculo — Agente Inteligente de Pesquisa em Arquivos

🔗 **Acesse online:** [guiirios.github.io/oraculo](https://guiirios.github.io/oraculo/)

O **Oráculo** é um assistente de IA leve, prático e **100% client-side** (roda direto no navegador em um único `index.html`, sem precisar instalar servidor) que lê arquivos de uma pasta local e responde em formato de chat com busca semântica via **API do Google Gemini**.

---

## ✨ Funcionalidades

- **Leitura de pasta local:** suporta `.txt`, `.py`, `.md`, `.csv`, `.json`, `.pdf`, `.docx` (Word) e arquivos de código em geral.
- **Busca Semântica (RAG + Gemini):** entende contexto, relações e sinônimos mesmo quando a palavra exata não está no arquivo.
- **Respostas ao vivo (Streaming):** escreve palavra por palavra no chat, com memória de conversa.
- **Trechos curtos + Download direto:** exibe apenas o trecho relevante encontrado e libera o botão **⬇️ Baixar arquivo** para o documento original.
- **Modo Híbrido:** funciona imediatamente com **Busca Local** (sem precisar de chave) ou com **IA Gemini Ativa** (colando uma chave gratuita do Google AI Studio).
- **Tema Claro / Escuro:** alternância com 1 clique.

---

## 🏗️ Arquitetura

```text
  [ 👤 Usuário + Pasta Local ]
  (.txt, .py, .pdf, .docx, etc.)
                │
                ▼
  ┌───────────────────────────────────────────────┐
  │   🌐 Navegador (1 único arquivo: index.html)  │
  │                                               │
  │  1. Interface (HTML + CSS): Chat + Sidebar    │
  │  2. Leitor Local (JS + pdf.js + mammoth.js):  │
  │     lê os arquivos direto na memória do PC    │
  │  3. Buscador + Catálogo: monta prévia dos     │
  │     arquivos e filtra os trechos relevantes   │
  └──────────────────────┬────────────────────────┘
                         │  (HTTPS + Chave API)
                         ▼
  ┌───────────────────────────────────────────────┐
  │       🧠 API do Google Gemini (Nuvem)         │
  │                                               │
  │  • Recebe: Instruções + Catálogo + Pergunta   │
  │  • Entende contexto, relações e sinônimos     │
  │  • Devolve resposta ao vivo (Streaming SSE)   │
  └──────────────────────┬────────────────────────┘
                         │
                         ▼
  [ 💬 Resposta no Chat + Trecho curto + ⬇️ Download ]
```

---

## 🚀 Como usar

1. Acesse online em **[guiirios.github.io/oraculo](https://guiirios.github.io/oraculo/)** (ou abra o arquivo **`index.html`** no Chrome/Edge).
2. Clique em **📂 Selecionar Pasta** na barra lateral esquerda e aponte para uma pasta (você pode testar usando `documentos_exemplo/` ou `filmes_exemplo/`).
3. *(Opcional)* Para ativar as respostas com IA, gere uma chave gratuita em [aistudio.google.com/apikey](https://aistudio.google.com/apikey) e cole no campo **"Chave API Gemini"** no canto inferior esquerdo.
4. Converse normalmente no chat!

---

## 🔒 Segurança e Privacidade

- Nenhuma chave de API fica armazenada no código-fonte: a chave informada é salva apenas localmente no navegador do usuário (`localStorage`).
- Os arquivos selecionados são lidos diretamente no navegador do usuário.

---

## 🛠️ Tecnologias Utilizadas

- **HTML5, CSS3 e JavaScript (Vanilla)** — arquitetura zero-instalação em arquivo único
- **Google Gemini API** (`streamGenerateContent` com `systemInstruction`)
- **PDF.js** (leitura de arquivos `.pdf` no navegador)
- **Mammoth.js** (leitura de arquivos `.docx` no navegador)

---

## 👤 Autor

Criado por **Guilherme Rios** — [GitHub (@guiirios)](https://github.com/guiirios)
