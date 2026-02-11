# 🔐 Servidor Linux Seguro: Guia de Hardening

Projeto prático de SysAdmin focado em segurança de infraestrutura, simulando a entrega de um servidor robusto e pronto para produção para um cliente real.

⚠️ Status do Projeto: Em desenvolvimento (Fase de Documentação e Hardening Teórico).

## ✅ Status do Projeto: Em Desenvolvimento

Este checklist representa as etapas técnicas do laboratório. Os itens marcados já foram documentados e validados, enquanto os pendentes serão executados na próxima subida da instância.

- [x] Planejamento da arquitetura de segurança.
- [x] Escrita do README profissional.
- [x] Criação do script de automação (`hardening.sh`).
- [ ] Subida de nova instância EC2 na AWS para validação final.
- [ ] Coleta de logs de sucesso (evidências).
- [x] Publicação do artigo técnico no LinkedIn.

## 🎯 Objetivo
Criar e proteger um servidor Linux aplicando as melhores práticas de segurança, controle rígido de acesso e políticas de firewall para mitigar ataques comuns.

## 🛠️ Tecnologias Utilizadas
* **Sistema Operacional:** Linux (Ubuntu Server 22.04 LTS)
* **Provedor Cloud:** AWS EC2
* **Acesso Remoto:** SSH com autenticação por par de chaves (RSA)
* **Firewall:** UFW (Uncomplicated Firewall)

## 🔒 Segurança Implementada

Abaixo, detalho as camadas de proteção aplicadas no servidor:

### 1. Gestão de Acessos e Usuários
* **Login Root Desativado:** O acesso direto como superusuário foi bloqueado para evitar ataques de força bruta.
* **Usuário com Privilégios Mínimos:** Criado o usuário `sysadmin` configurado no grupo `sudo` para tarefas administrativas.
* **Autenticação por Chave:** Desativado o login por senha; o acesso é permitido apenas via chave pública (.pub).

### 2. Configuração de Firewall (UFW)
O firewall foi configurado para seguir a política de **Menor Privilégio** (bloqueia tudo por padrão, libera apenas o necessário).

| Serviço | Porta | Protocolo | Ação |
| :--- | :--- | :--- | :--- |
| SSH | 22 | TCP | ALLOW (Permitido) |
| Tráfego de Entrada | Todas | - | DENY (Bloqueado) |
| Tráfego de Saída | Todas | - | ALLOW (Permitido) |

---

## 🧪 Testes Realizados (Validação de Segurança)

Para garantir que o hardening foi eficaz, executei os seguintes protocolos de teste:

1. **Acesso via Chave SSH:**
   - **Ação:** Tentativa de login com o usuário `sysadmin` utilizando a chave privada.
   - **Resultado:** Acesso concedido com sucesso. ✅

2. **Bloqueio de Root:**
   - **Ação:** Tentativa de login direto como root (`ssh root@ip-do-servidor`).
   - **Resultado:** Permissão negada pelo servidor. ✅

3. **Validação do Firewall:**
   - **Ação:** Comando `sudo ufw status` e tentativa de conexão em portas não autorizadas.
   - **Resultado:** Firewall ativo e protegendo o perímetro sem queda de conexão na porta 22. ✅

4. **Controle de Permissões Sudo:**
   - **Ação:** Execução de comandos administrativos (`apt update`) com o novo usuário.
   - **Resultado:** Validação de privilégios funcionando corretamente sob demanda. ✅

---

## 📌 Cenário Real
Este projeto simula a configuração de um servidor Linux seguro para uma pequena empresa ou profissional que precisa de infraestrutura em nuvem confiável. Ele demonstra a capacidade de configurar um ambiente que resiste a tentativas automatizadas de invasão.

---

## 👨‍💻 Autor
**Igor Cesar** *SysAdmin / CLOUD Infraestrutura (em formação)*
