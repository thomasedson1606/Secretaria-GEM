# Controle SAM - Secretaria GEM CCB 🎵

Aplicação web moderna, intuitiva e responsiva desenvolvida para a administração musical e conferência semanal de lançamentos do **SAM (Sistema de Administração Musical - CCB)** pelas secretarias do Grupo de Estudo Musical (GEM).

---

## 🚀 Funcionalidades Principais

- **Lançamento e Auditoria Semanal por Comum Congregação:**
  - 1. **Cadastro de Membros:** Músicos, organistas, instrutores e candidatos.
  - 2. **Cadastro de Alunos:** Enturmação e status MSA.
  - 3. **Cadastro de Turmas:** Fases e turmas ativas do GEM.
  - 4. **Aula da Semana:** Lançamentos de chamada/presença e matérias ministradas.
- **Indicador Visual de Progresso:**
  - Percentual dinâmico de comuns 100% concluídas, pendentes e com pendências parciais.
- **Sincronização em Nuvem (Firebase Firestore):**
  - Dados compartilhados em tempo real entre secretários e dispositivos.
  - Modo híbrido com suporte offline e fallback transparente para `localStorage`.
- **Exportações e Relatórios:**
  - 📱 **Resumo Formatado para WhatsApp:** Com emojis, status por comum e contagem total, copiado com 1 clique.
  - 📊 **Exportação Excel (.xlsx):** Planilha detalhada da semana selecionada ou histórico consolidado.
  - 🖨️ **Impressão Otimizada:** Folha de conferência formatada sem botões ou menus.
- **Painel Administrativo Completo (Configuração):**
  - Cadastro de Comuns Congregações e Secretário do GEM responsável.
  - Cadastro de Secretários Conferentes.
  - Cadastro de Datas de Análise Semanal.
  - Backup e Restauração em formato `.json`.

---

## 🔥 Configuração do Firebase Firestore

A aplicação está integrada com o **Firebase Firestore** para sincronização multi-usuário em tempo real.

### Regras de Segurança (`firestore.rules`)
```javascript
rules_version = '2';

service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.time < timestamp.date(2028, 12, 23);
    }
  }
}
```

### Como Conectar à Nuvem
1. No menu superior da aplicação, acesse a aba **Configuração** > **Nuvem & Firebase** (ou clique no badge de status do Firebase no topo).
2. Cole as credenciais do seu projeto Firebase obtidas em *Project Settings* > *General* > *Web Apps* no Console do Firebase (`apiKey`, `projectId`, `authDomain`, `appId`).
3. Clique em **Salvar & Conectar ao Firebase**.
4. Use o botão **Subir dados locais para a Nuvem** para sincronizar seus cadastros existentes.

---

## 💻 Como Rodar Localmente

Basta abrir o arquivo `index.html` em qualquer navegador web moderno (Google Chrome, Edge, Firefox, Safari).

---

## 🌐 Deploy no GitHub Pages

1. Acesse o repositório [Secretaria-GEM](https://github.com/thomasedson1606/Secretaria-GEM).
2. Vá em **Settings** > **Pages**.
3. Em **Branch**, selecione `main` e a pasta `/(root)`.
4. Clique em **Save**. O site estará disponível em `https://thomasedson1606.github.io/Secretaria-GEM/`.

---

## ☁️ Deploy no Firebase Hosting

Se preferir publicar no Firebase Hosting:
```bash
npm install -g firebase-tools
firebase login
firebase init
firebase deploy
```

---

## 📂 Estrutura do Projeto

```
SECRETARIA/
├── index.html                           # Aplicação web principal completa
├── controle_de_confer_ncia_sam_ccb.html  # Arquivo original de referência
├── firestore.rules                      # Regras de segurança do Firestore
├── firebase.json                        # Configuração de Hosting e Firestore
├── .gitignore                           # Arquivos ignorados pelo Git
└── README.md                            # Documentação do projeto
```
