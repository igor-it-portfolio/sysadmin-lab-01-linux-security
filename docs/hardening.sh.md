#!/bin/bash

# ---------------------------------------------------------
# SCRIPT DE HARDENING BÁSICO - PROJETO LINUX SEGURO
# Autor: Igor Cesar
# ---------------------------------------------------------

# 1. Atualização do Sistema
echo "Iniciando atualizações do sistema..."
sudo apt update && sudo apt upgrade -y

# 2. Configuração de Firewall (UFW)
echo "Configurando Firewall (UFW)..."
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw --force enable

# 3. Hardening de SSH
echo "Desativando login de root no SSH..."
# O comando sed edita o arquivo diretamente trocando 'yes' por 'no'
sudo sed -i 's/PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
sudo systemctl restart ssh

echo "Configuração concluída com sucesso!"
