# 🚢 Luxo — Aluguel de Iates

Projeto web estático desenvolvido como atividade acadêmica, com integração a uma API externa para envio e leitura de mensagens de contato, além de autenticação de usuário administrador.

---

## 📁 Estrutura do Projeto

    projeto-iates/
    ├── index.html
    ├── aluguel.html
    ├── destinos.html
    ├── tripulacao.html
    ├── contato.html        ← 1ª implementação
    ├── admin.html          ← 2ª implementação (nova página)
    ├── mensagens.html      ← 3ª implementação (nova página)
    ├── css/
    │   └── default.css
    ├── js/
    │   ├── jquery-3.6.4.min.js
    │   └── api.js
    └── images/
        └── ...

---

## ⚙️ Funcionalidades Implementadas

### 1ª Implementação — Formulário de Contato (`contato.html`)

Ao clicar no botão **Enviar**, os valores dos campos Nome, E-mail e Mensagem são capturados e enviados à API por meio da função `inserirMensagem(mensagem)`, definida em `api.js`.

O objeto enviado segue o formato:

```javascript
var mensagem = {
    nome: "nome da pessoa",
    email: "email informado",
    mensagem: "a mensagem informada"
}
```

---

### 2ª Implementação — Login Administrativo (`admin.html`)

Página de autenticação com campos de **E-mail** e **Senha**. Utiliza a função `validarUsuario(objLoginSenha)` da `api.js` para verificar as credenciais.

- Se válidas → redireciona para `mensagens.html`
- Se inválidas → exibe a mensagem **"E-mail e Senha inválidos"**

O objeto de autenticação segue o formato:

```javascript
var objLoginSenha = {
    email: "email informado",
    senha: "senha informada"
}
```

Credenciais de acesso:
- **E-mail:** admin@admin.com
- **Senha:** 1234

---

### 3ª Implementação — Visualização de Mensagens (`mensagens.html`)

Página restrita ao administrador. Ao carregar, chama a função `obterMensagens()` da `api.js`, que retorna um array de objetos com todas as mensagens recebidas. Os dados são exibidos dinamicamente em uma tabela com as colunas: **#, Nome, E-mail e Mensagem**.

---

## 🔌 API Utilizada

Base URL: `https://app-p2-js-ce71c114995f.herokuapp.com`

| Função | Método | Endpoint |
|---|---|---|
| `obterMensagens()` | GET | `/mensagens` |
| `inserirMensagem(obj)` | POST | `/mensagens` |
| `validarUsuario(obj)` | POST | `/usuarios/validar` |

---

## 📦 Dependências

- jQuery 3.6.4 (incluído localmente em `js/jquery-3.6.4.min.js`)
- `api.js` (funções de integração com a API)

Os scripts devem ser importados **nesta ordem** em todas as páginas que utilizam a API:

```html
<script src="js/jquery-3.6.4.min.js"></script>
<script src="js/api.js"></script>
```

---

## 🚀 Como executar

Por se tratar de um projeto estático com chamadas AJAX, recomenda-se utilizar um servidor local para evitar bloqueios de CORS. Algumas opções:

- Extensão **Live Server** no VS Code
- `npx serve .` via terminal
- Qualquer outro servidor HTTP local

Abra o arquivo `index.html` pelo servidor local para navegar pelo site.
