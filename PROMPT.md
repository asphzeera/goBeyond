Aqui está um **Super Prompt** estruturado que você pode copiar e colar em qualquer IA de programação (como Cursor, GitHub Copilot, ChatGPT ou Claude) para que ela construa o seu MVP.

Eu dividi o prompt em duas partes: a arquitetura do aplicativo em si e o **System Prompt** (o cérebro da IA que vai rodar dentro do seu app).

---

### Copie e cole o texto abaixo na sua IA de programação:

**Contexto:**
Você é um Desenvolvedor Mobile Sênior e Especialista em UX/UI Minimalista. Sua missão é criar o MVP (Minimum Viable Product) de um aplicativo chamado **goBeyond**. Eu serei o único usuário (cobaia) deste MVP.

**Conceito do App:**
O goBeyond é um app focado no autodidatismo e mudança de identidade. Ele usa a lógica de controle em malha fechada (closed-loop): o usuário define um objetivo abstrato, a IA quebra isso em uma tarefa diária minúscula (irrisória), o usuário executa, dá um feedback de dificuldade (1 a 5), e a IA calibra a tarefa do dia seguinte para manter o usuário no "Estado de Fluxo" e não depender de motivação (usando o Modelo de Fogg B=MAP).

**Requisitos Técnicos do MVP:**

1. **Linguagem/Framework:** Escolha o melhor framework com foco mobile para desenvolvimento rápido (sugiro Flutter ou React Native com Expo).
2. **Armazenamento:** Tudo pode ser salvo localmente no dispositivo (AsyncStorage/SharedPreferences/SQLite) já que é um MVP de uso pessoal.
3. **Integração de IA:** O app deve ter um arquivo de configuração/serviço pronto para eu inserir minha chave de API (Gemini ou OpenAI) e fazer as chamadas REST.
4. **Interface (UI Minimalista - Foco na Ação):**
* **Tela 1: Onboarding do Objetivo.** Dois campos de texto: "O que você quer alcançar?" e "Por que isso é importante para quem você quer se tornar?".
* **Tela 2: A Tarefa do Dia (Dashboard).** Mostra a tarefa calibrada pela IA para hoje de forma grande e clara.
* **Tela 3: Feedback (O Quebra Nozes).** Ao fim do dia, o usuário responde: "Você concluiu?" (Sim/Parcial/Não) e "Qual foi a dificuldade de executar?" (Escala de 1 a 5, onde 1 é muito fácil e 5 é exaustivo). Ao enviar, o app chama a API da IA para gerar a tarefa de amanhã.



**O Prompt de Sistema da IA (System Prompt):**
Implemente o seguinte prompt no backend/serviço de IA do aplicativo para quando ele for consultar a próxima tarefa. Ele deve receber as variáveis do dia e retornar APENAS o texto da próxima tarefa.

```text
Você é o motor de calibração do goBeyond. Sua função é aplicar a Teoria do Fluxo e o Modelo Comportamental de Fogg (B=MAP).
O usuário quer construir o hábito de: {objetivo_do_usuario}
O motivo profundo dele é: {motivo_do_usuario}

Ontem, a tarefa dele foi: "{tarefa_anterior}"
O resultado da execução foi: {status_de_conclusao}
A dificuldade relatada foi: {dificuldade_1_a_5} (1 = Muito fácil, 5 = Muito difícil/Exaustivo).

Regras de Calibração:
- Se a dificuldade foi 4 ou 5, a carga cognitiva está muito alta. REDUZA a tarefa para amanhã (ex: de ler 5 páginas, passe para 2). O objetivo é não quebrar o hábito.
- Se a dificuldade foi 1 ou 2 e foi concluída, a tarefa está fácil. AUMENTE LEVEMENTE para gerar progresso, mas sem exageros.
- Se a dificuldade foi 3, MANTENHA o mesmo nível.
- Se não foi concluída, REDUZA DRASTICAMENTE a tarefa para o nível irrisório (Mínimo Produto Viável do Hábito) para recuperar a inércia.
- Não dê explicações, conselhos ou mensagens motivacionais. 

Retorne APENAS a instrução clara e direta da tarefa para hoje.

```

**Instruções de Saída para o Desenvolvedor:**
Por favor, gere:

1. A estrutura de pastas do projeto.
2. O código dos componentes de UI (minimalistas, tema escuro recomendado para foco).
3. O serviço de API (`ai_service`) que recebe as variáveis, injeta no System Prompt acima e faz a chamada HTTP.
4. O gerenciador de estado simples para salvar o progresso e a tarefa atual localmente.

---

### Como usar isso agora?

1. Se você for usar uma ferramenta como **Cursor** (um editor de código com IA que recomendo muito para quem não é programador de ofício, pois ele escreve nos arquivos para você) ou o **Claude/ChatGPT**, basta colar esse texto acima.
2. Ele vai te cuspir o código completo e te dar as instruções de como rodar no seu celular (através do Expo Go, se for React Native, por exemplo).
3. O **System Prompt** que escrevi no bloco de código já embute toda a ciência que discutimos (Sweller, Fogg e Flow) em regras matemáticas que a IA consegue processar.

Você quer que eu aprofunde a lógica de algum desses passos de feedback ou podemos considerar essa a sua largada para os testes em si mesmo?
