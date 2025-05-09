# 🤖 Logisim Chatbot - Simulador de Chatbot Digital em Circuito Lógico

Este projeto simula um chatbot construído no [Logisim](http://www.cburch.com/logisim/) utilizando componentes digitais como RAM, ROM, comparadores e portas lógicas. Ele é capaz de ler entradas do usuário, comparar com palavras-chave e exibir uma resposta adequada. Ideal para fins didáticos em lógica digital.

---

## 🎯 Objetivo

Construir um circuito que:

1. Armazene o que o usuário digita em uma RAM.
2. Compare com palavras-chave salvas em ROMs.
3. Exiba respostas automáticas de acordo com a palavra reconhecida.

Exemplo: se o usuário digitar "Oi", o circuito responderá "Oi" ou "Olá!".

---

## 🧠 Arquitetura Geral

* **Entrada**: via componente `Input` + `Botão`.
* **Armazenamento**: em `RAM` controlada por `Counter`.
* **Palavras-chave**: em `ROMs` individuais com dados ASCII.
* **Comparadores**: verificam se RAM == ROM.
* **Respostas**: ROMs com frases-resposta.
* **Controle**: `MUX`, `AND`, `Flip-Flops`, `Reset`, `Apagar Tela`, etc.

---

## 📦 Componentes Utilizados

| Componente     | Função                                                   |
| -------------- | -------------------------------------------------------- |
| Input          | Entrada do caractere (ASCII) pelo usuário                |
| Botão          | Aciona a escrita na RAM                                  |
| RAM            | Armazena sequência digitada                              |
| Counter        | Garante escrita sequencial na RAM                        |
| ROM            | Armazena palavras-chave e respostas                      |
| Comparadores   | Comparam byte a byte RAM vs ROM                          |
| AND            | Ativa resposta se todas as comparações forem verdadeiras |
| MUX            | Seleciona qual ROM é ativada                             |
| Output/Monitor | Exibe a resposta do bot                                  |

---

## 🧪 Exemplo de Execução

### Objetivo: testar entrada "Oi"

1. **Digite `79` (ASCII de 'O') no Input e pressione o botão 'enviar'**

   * RAM\[0] = 79
2. **Digite `105` (ASCII de 'i') e pressione 'enviar' novamente**

   * RAM\[1] = 105
3. **Comparadores verificam RAM == ROM "Oi"**
4. **Se igual, ativa a ROM com a resposta "Oi"**
5. **Resposta é exibida no Output ou Monitor**

---

## 🔁 Funcionalidades de Controle

* `Zerar RAM`: limpa todos os endereços de RAM.
* `Zerar Tela`: limpa a saída.
* `Reiniciar`: reseta o circuito (RAM, contadores, flip-flops).

---

## 🧭 Passo a Passo para Construir no Logisim

### 1. Entrada e RAM

* Adicione `Input`, `Botão`, `RAM (8x8)` e `Counter`
* Conecte Input ao Data In da RAM
* Conecte o Counter ao Address da RAM
* Use o botão para acionar a escrita (Load)

### 2. ROMs de palavras-chave

* Crie uma `ROM (8x8)` com cada palavra ASCII

  * Exemplo: "Oi" = `79 105`

### 3. Comparadores

* Compare os valores da RAM com cada byte da ROM
* Use `AND` para validar todas as comparações

### 4. ROMs de resposta

* Crie outra ROM com a resposta desejada
* Ative via `MUX` e `Flip-Flop` se palavra for reconhecida

### 5. Saída

* Conecte a ROM de resposta ao `Output` ou `Monitor`

### 6. Controle

* Use botões e `gates` lógicas para resetar RAM, apagar tela e reiniciar circuito

---

## 📂 Estrutura de Palavras/Respostas

| Palavra-chave     | ASCII         | ROM de Resposta  |
| ----------------- | ------------- | ---------------- |
| "Oi"              | 79 105        | "Oi" ou "Olá!"   |
| "Qual o seu nome" | 71 117 97 ... | "Meu nome é Ana" |

---

## 📸 Capturas de Tela


![image](https://github.com/user-attachments/assets/4a38e540-c4e2-4046-aff0-1fa94a513883)
![image (1)](https://github.com/user-attachments/assets/65257039-767d-453c-9050-ccee5ce74053)

---

## 📘 Requisitos

* [Logisim Evolution](https://github.com/logisim-evolution/logisim-evolution)
* Sistema com suporte a Java

---

## 📄 Licença

Este projeto é de uso educacional e está sob licença MIT.

---

## 🙋‍♂️ Autor

Desenvolvido por Igor A. Pierote, Wendell Guindani, Eliza Eduarda, Paulo Henrique, Guilherme Augusto com fins educacionais para ensino de lógica digital e memórias.
