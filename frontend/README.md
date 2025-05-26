
# InfraAlert - Guia de Configuração e Execução

## 🧭 Introdução

Este documento descreve os passos necessários para configurar e executar o projeto **InfraAlert**. O projeto é composto por:

- **Front-end**: Aplicativo mobile desenvolvido com **React Native** e **Expo**.
- **Back-end**: API RESTful desenvolvida com **Node.js**, **Express**, **TypeScript** e **Prisma**, utilizando **PostgreSQL** como banco de dados.

---

## 📁 Estrutura do Projeto

```
InfraAlert/
├── InfraAlert/        # Diretório do Front-end (React Native / Expo)
│   ├── App.js
│   ├── package.json
│   ├── telas/
│   │   ├── AdminScreen.js
│   │   ├── Cadastro.js
│   │   └── Login.js
│   └── ... (outros arquivos)
├── backend/           # Diretório do Back-end (Node.js / Prisma)
│   ├── src/
│   ├── prisma/
│   ├── package.json
│   ├── tsconfig.json
│   ├── .env.example
│   └── ... (outros arquivos)
└── README.md          # Este documento
```

---

## ✅ Requisitos

Certifique-se de ter os seguintes softwares instalados:

- [Node.js](https://nodejs.org/) (versão LTS recomendada)
- Expo CLI: `npm install -g expo-cli`
- App **Expo Go** no celular (disponível na Play Store/App Store)
- PostgreSQL (banco de dados ativo e acessível)

---

## ⚙️ Configuração do Back-end

Acesse o diretório `backend`:

```bash
cd backend
```

### 🔐 Variáveis de Ambiente

```bash
cp .env.example .env
```

- Edite o arquivo `.env` criado.
- Configure `DATABASE_URL` no formato:

```
postgresql://USUARIO:SENHA@HOST:PORTA/NOME_DO_BANCO
```

### 📦 Instalação de Dependências

```bash
npm install
```

### 🔧 Gerar Cliente Prisma

```bash
npx prisma generate
```

### 🛠 Aplicar Migrações no Banco

```bash
npx prisma migrate dev
```

---

## 📲 Configuração do Front-end

Acesse o diretório do front-end:

```bash
cd ../frontend
```

### 📦 Instalar Dependências

```bash
npm install
```

> Se ocorrerem erros de dependências:
```bash
npm install --legacy-peer-deps
```

### 🌐 Configurar a URL da API

Nos arquivos `AdminScreen.js`, `Cadastro.js`, `Login.js`, altere a constante `API_URL` conforme seu ambiente:

- Simulador iOS (Mac):
  ```js
  const API_URL = 'http://localhost:3000/api';
  ```

- Emulador Android:
  ```js
  const API_URL = 'http://10.0.2.2:3000/api';
  ```

- Celular físico (via Expo Go):
  ```js
  const API_URL = 'http://SEU_IP_LOCAL:3000/api';
  ```

Use `ipconfig` (Windows) ou `ifconfig/ip addr` (Mac/Linux) para descobrir seu IP local.

---

## 🚀 Executando o Projeto

### 1. Iniciar o Back-end

```bash
cd backend
npm run dev
```

### 2. Iniciar o Front-end

Em um novo terminal:

```bash
cd InfraAlert
npx expo start
```

Você poderá:

- Escanear o QR Code com o app Expo Go
- Rodar em emulador Android: `npx expo start --android`
- Rodar em emulador iOS (macOS): `npx expo start --ios`
- Rodar no navegador: `npx expo start --web`

---

## 🧯 Solução de Problemas Comuns

### ❌ Erros de dependência

```bash
npm cache clean --force
npm install
```

Ou:

```bash
npm install --legacy-peer-deps
```

### ❌ Front-end não conecta ao Back-end

- Verifique se o back-end está rodando.
- Confirme a `API_URL` correta.
- Certifique-se de que ambos (emulador/dispositivo e máquina) estão na mesma rede.
- Verifique firewalls ou bloqueios.

### ❌ Problemas com Prisma

- Confirme o `.env`.
- Execute novamente:

```bash
npx prisma generate
npx prisma migrate dev
```

---

## 🧠 Por que meu projeto não está rodando?

Verifique cuidadosamente as configurações de ambiente, a conexão entre front e back-end, e siga as instruções passo a passo. Ainda com problemas? Volte para a seção "Solução de Problemas Comuns".

---

InfraAlert © 2025  
Desenvolvido por Júlio César Dourado  
