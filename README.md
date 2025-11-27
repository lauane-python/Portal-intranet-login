# 🔐 **ERS – Módulo de Login | Portal da Intranet**

![Status](https://img.shields.io/badge/status-em%20desenvolvimento-blue)  
![Node](https://img.shields.io/badge/Node.js-18.x-green?logo=node.js)  
![MySQL](https://img.shields.io/badge/MySQL-database-blue?logo=mysql)  
![License](https://img.shields.io/badge/license-MIT-lightgrey)

---

## 📘 **1. Introdução**

Este documento apresenta a Especificação de Requisitos do Sistema (ERS) para o módulo de Login da Intranet, definindo os processos de autenticação, validações no frontend e backend, regras de segurança e o fluxo completo de registro e acesso.  
O módulo contempla apenas as operações essenciais de login, sem funcionalidades adicionais de gerenciamento de contas.  
Serve como referência para desenvolvimento, testes, homologação e manutenção.

---

## 🎯 **1.1 Objetivo**

Garantir um processo de autenticação seguro e padronizado, assegurando integridade de dados e controle de acesso ao ambiente interno da empresa.

---

## 📌 **2. Escopo**

O módulo inclui:

- Exibição do formulário de login.  
- Validações de e-mail e senha no frontend.  
- Processamento e validações no backend.  
- Armazenamento seguro das credenciais.  
- Registro automático de data/hora.  
- Definição de status inicial do usuário.  
- Liberação de acesso somente após autenticação.

---

## 🚫 **3. Fora do Escopo**

- Recuperação de senha.  
- Alteração, edição ou exclusão de contas.  
- Cadastro aberto via interface.  
- Perfis de usuário e permissões.  
- Autenticação em duas etapas (MFA).  
- Envio de e-mails.  
- Páginas internas da intranet.

---

## ⚙️ **4. Requisitos Funcionais**

### **RF01 – Exibir formulário de login**  
Campos obrigatórios:
- E-mail  
- Senha  
- Botão Login  

### **RF02 – Validar e-mail no frontend**  
Bloquear o envio se:
- Campo vazio  
- Menos de 6 caracteres  

Mensagem esperada:  
> **"Preencha um email válido."**

### **RF03 – Validar senha no frontend**
O sistema deve bloquear o envio se a senha possuir **menos de 6 caracteres**.  
**Mensagem esperada:**  
"A senha tem que conter no mínimo 6 caracteres."

---

### **RF04 – Enviar dados para o backend**
Ao clicar em **"Login"**, o frontend deve enviar uma requisição **POST** para:  
`http://localhost:3000/login`

**Conteúdo enviado:**
- email  
- senha  

---

### **RF05 – Verificar existência do e-mail (backend)**
O backend deve consultar a tabela **login** para verificar se o e-mail já está cadastrado.  
Se o e-mail existir, retornar:  
"Email já cadastrado."

---

### **RF06 – Criptografar a senha**
Antes de armazenar a senha, o servidor deve gerar um **hash com bcrypt (10 rounds)**.

---

### **RF07 – Registrar novo usuário no banco**
O backend deve inserir:
- email  
- senha (hash)  
- criado_em (timestamp automático)  
- status_lei = "Aguardando resposta"  

---

### **RF08 – Mensagem de sucesso**
Se o cadastro for concluído, retornar:  
"Cadastro realizado com sucesso."

---

### **RF09 – Exibir o retorno do servidor**
O frontend deve exibir ao usuário a mensagem retornada pelo backend.

---

## 2. Regras de Negócio

### **RN01 – Armazenamento seguro de senha**
Nenhuma senha poderá ser armazenada em texto puro.

### **RN02 – E-mail único**
O e-mail é um identificador único; não podem existir registros duplicados.  

### **RN03 – Status padrão**
Novo registro deve receber o status: **"Aguardando resposta"**

### **RN04 – Registro de data/hora**
A criação do login deve ser registrada automaticamente no campo **criado_em**.

---

## 3. Restrições do Sistema

- Backend em **Node.js + Express**  
- Banco de dados **MySQL/MariaDB**  
- Frontend em **HTML, CSS e JavaScript**  
- Requisições em formato **JSON**  
- Sistema rodando na porta **3000**  
- Hashing de senha com **bcrypt**

---

## 4. Fluxo Principal

1. Usuário acessa a página de login.  
2. Preenche e-mail e senha.  
3. Frontend valida os dados.  
4. Envia requisição ao backend.  
5. Backend valida novamente.  
6. Verifica se o e-mail já existe.  
7. Gera o hash da senha.  
8. Salva no banco de dados.  
9. Backend retorna resposta.  
10. Frontend exibe ao usuário.

---

## 5. Considerações Finais
Este documento reúne todas as especificações para o módulo de **Login da Intranet**, servindo de base para desenvolvimento, testes, homologação e manutenções futuras.

---
