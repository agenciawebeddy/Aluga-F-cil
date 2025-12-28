# Regras de Edição e Stack Tecnológico (AutoFix CRM)

Este documento define o stack tecnológico e as regras de utilização de bibliotecas para garantir a consistência e manutenibilidade do projeto.

## Stack Tecnológico

*   **Framework:** React (Componentes funcionais e Hooks).
*   **Linguagem:** TypeScript.
*   **Roteamento:** React Router DOM (v6+).
*   **Estilização:** Tailwind CSS (abordagem utility-first).
*   **Tema:** Customização de tema via variáveis CSS (`--primary-xxx`) gerenciadas pelo utilitário `applyTheme`.
*   **Ícones:** `lucide-react`.
*   **Backend/Dados:** Supabase (acessado através da camada de serviço `mockService`).
*   **Inteligência Artificial:** Google GenAI SDK (`@google/genai`).
*   **Gráficos:** Recharts.
*   **Geração de Documentos:** `jspdf` e `jspdf-autotable` para relatórios e orçamentos.

## Regras de Utilização de Bibliotecas

Para manter a consistência e a qualidade do código, siga estas diretrizes ao implementar novas funcionalidades ou modificar as existentes:

1.  **Componentes e Estrutura:**
    *   Sempre utilize componentes funcionais e hooks do React.
    *   Novos componentes devem ser criados em arquivos separados (`src/components/`).
    *   As páginas principais devem residir em `src/pages/`.

2.  **Estilo e UI:**
    *   **NÃO** utilize CSS puro ou módulos CSS. A estilização deve ser feita **exclusivamente** com classes utilitárias do Tailwind CSS.
    *   Para cores primárias, utilize as classes dinâmicas do Tailwind que mapeiam para as variáveis CSS (`bg-primary-600`, `text-primary-700`, etc.).
    *   Utilize `lucide-react` para todos os ícones.

3.  **Dados e Backend:**
    *   Todas as operações de CRUD (Create, Read, Update, Delete) devem ser encapsuladas e executadas através das funções definidas em `services/mockData.ts` (que utiliza o Supabase).
    *   O tema da aplicação deve ser gerenciado e aplicado usando a função `applyTheme` de `services/mockData.ts`.

4.  **Funcionalidades Específicas:**
    *   **Roteamento:** Use os componentes `Link`, `Routes` e `Route` de `react-router-dom`.
    *   **Gráficos:** Use a biblioteca Recharts para todas as visualizações de dados.
    *   **PDFs:** Use `jspdf` e `jspdf-autotable` para gerar documentos (orçamentos, relatórios).
    *   **IA:** A integração com a IA deve ser feita através da função `generateDiagnosis` em `services/geminiService.ts`.