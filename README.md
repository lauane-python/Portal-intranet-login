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
Bloquear envio se:
- Menos de 6 caracteres
