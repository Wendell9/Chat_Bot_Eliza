# 🤖 Logisim Chatbot - Simulador de Chatbot Digital em Circuito Lógico

Este projeto simula um chatbot construído no [Logisim Evolution](https://github.com/logisim-evolution/logisim-evolution), utilizando circuitos lógicos digitais. O objetivo é criar um sistema que capture a entrada do usuário, armazene na RAM, compare com palavras-chave em ROMs e, em caso de correspondência, exiba uma resposta automática na tela.

Ideal para estudos de lógica digital, automação e projetos educacionais.

---

## 🎯 Objetivo Geral

Construir um circuito 100% funcional em Logisim que:

1. Armazena caracteres digitados pelo usuário (em ASCII) na RAM.
2. Usa ROMs contendo palavras-chave e respostas automáticas.
3. Compara a entrada com as palavras-chave.
4. Exibe uma resposta ao detectar uma correspondência.

Exemplo: se o usuário digitar `Oi`, o chatbot responde `Olá!`.

---

## 🧩 Componentes e Módulos Principais

| Módulo         | Função                                                                |
| -------------- | --------------------------------------------------------------------- |
| Entrada        | Recebe um caractere do usuário (ASCII)                                |
| RAM            | Armazena a sequência de caracteres inseridos                          |
| Counter        | Define o endereço da RAM onde o próximo caractere será gravado        |
| ROM (palavras) | Contém as palavras-chave que o chatbot é capaz de reconhecer          |
| Comparadores   | Comparam byte a byte o conteúdo da RAM com as ROMs                    |
| Lógica AND     | Valida se todos os bytes de uma palavra foram corretamente comparados |
| ROM (resposta) | Armazena a mensagem a ser exibida ao detectar correspondência         |
| MUX            | Direciona qual ROM de resposta deve ser ativada                       |
| Output         | Exibe o conteúdo da ROM de resposta                                   |
| Botões         | Controlam o fluxo: Enviar, Zerar RAM, Reiniciar, Apagar Tela etc.     |

---

## 🔁 Funcionamento Geral do Circuito

1. O usuário insere um caractere (ex: `O`, código ASCII 79).
2. Pressiona o botão `Enviar`, gravando o valor na RAM na posição atual do contador.
3. O contador incrementa automaticamente, pronto para o próximo caractere.
4. Ao completar uma palavra (ex: `Oi` = 79, 105), o sistema automaticamente realiza as comparações com todas as ROMs de palavras-chave.
5. Se uma ROM casar com os valores da RAM, o circuito ativa a ROM de resposta correspondente.
6. O conteúdo da ROM de resposta é exibido na tela (via `Output` ou `TTY`).

---

## 🛠️ Passo a Passo de Implementação no Logisim

### 🔹 ETAPA 1: Entrada e Armazenamento na RAM

1. **Adicione um componente `Input` (8 bits)**: esse será o campo de entrada do caractere ASCII.
2. **Adicione um `Button` e conecte ao sinal de `Load` da RAM**: ao pressionar o botão, o valor do input será gravado.
3. **Insira um `Counter` (3 bits)**: sua saída será conectada ao `Address` da RAM.
4. **Adicione uma `RAM (8x8)`**:

   * `Data In` vem do `Input`
   * `Address` vem do `Counter`
   * `Load` é controlado pelo botão
5. **Conecte uma saída da RAM para observação (via split ou wire direto)**
6. Toda vez que o botão é pressionado:

   * O valor do input é gravado no endereço atual
   * O contador é incrementado automaticamente para o próximo endereço

### 🔹 ETAPA 2: Palavras-chave em ROMs

1. **Adicione uma `ROM` para cada palavra-chave**:

   * Ex: ROM "Oi" conterá valores: `79` (O), `105` (i)
   * Insira os valores manualmente no editor da ROM
   * Configure a ROM com 8 endereços (se cada palavra tiver até 8 letras)
2. **Conecte a saída da RAM aos comparadores**
3. **Adicione comparadores `==` para cada byte da palavra**:

   * Compare `RAM[0]` com `ROM[0]`
   * Compare `RAM[1]` com `ROM[1]`, e assim por diante
4. **Adicione uma porta `AND`**:

   * Ela receberá a saída de todos os comparadores da palavra
   * Se todas forem verdadeiras, a palavra foi reconhecida

### 🔹 ETAPA 3: ROMs de Resposta

1. **Crie uma `ROM` para cada resposta que o chatbot dará**

   * Ex: Para palavra "Oi", ROM com "Olá!" (ASCII: 79, 108, 225, 33...)
2. **Use um `MUX` para escolher entre várias ROMs de resposta**

   * A seleção será feita com base na porta AND ativada
3. **Adicione um contador para ler os bytes da ROM de resposta**

   * Ele deve ler sequencialmente os bytes após o reconhecimento da palavra
4. **Conecte a saída da ROM ao `Output` ou `TTY`**

   * Os valores serão exibidos byte a byte

### 🔹 ETAPA 4: Controles Adicionais

1. **Zerar RAM**:

   * Use um botão que aciona um circuito que grava `0` em todos os endereços
2. **Zerar Tela**:

   * Botão que zera o `Output`
3. **Reiniciar**:

   * Reseta contador, flip-flops, RAM e lógica
4. **Adicionar LED de status** (opcional):

   * Indica quando uma palavra foi reconhecida ou resposta está ativa

---

## 💡 Dicas para Melhorar o Projeto

* Use `Tunnels` e `Labels` para organizar visualmente seu circuito
* Divida o circuito em subcircuitos: Entrada, Armazenamento, Comparação, Resposta
* Salve diferentes versões enquanto avança
* Teste com várias combinações e palavras
* Consulte: [https://www.asciitable.com/](https://www.asciitable.com/) para codificar suas palavras

---

## 🧪 Palavras-chave e Respostas de Exemplo

| Palavra-chave     | ASCII         | Resposta         | ASCII da Resposta |
| ----------------- | ------------- | ---------------- | ----------------- |
| "Oi"              | 79 105        | "Olá!"           | 79 108 225 33     |
| "Qual o seu nome" | 81 117 97 ... | "Meu nome é Ana" | 77 101 117 ...    |

---

## 🧾 Requisitos

* Logisim Evolution
* Conhecimento básico de ASCII e circuitos digitais

---

## 👨‍🏫 Autoria

Desenvolvido por Igor A. Pierote, Wendell Guindani, Eliza Eduarda, Paulo Henrique, Guilherme Augusto para fins educacionais.

---

## 📄 Licença

MIT License - Uso livre educacional.

---

## 📸 Capturas de Tela

![image](https://github.com/user-attachments/assets/4a38e540-c4e2-4046-aff0-1fa94a513883)
![image (1)](https://github.com/user-attachments/assets/65257039-767d-453c-9050-ccee5ce74053)
