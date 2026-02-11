#!/bash/bin

# ---------------------------------------------------------
# SCRIPT DE HARDENING BÁSICO - PROJETO LINUX SEGURO
# Autor: Igor Cesar
# ---------------------------------------------------------

echo "Iniciando atualizações do sistema..."
sudo apt update && sudo apt upgrade -y

echo "Configurando Firewall (UFW)..."
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo ufw --force enable

echo "Hardening de SSH..."
# O comando abaixo desativa o login de root no arquivo de config
sudo sed -i 's/PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
sudo systemctl restart ssh

echo "Configuração concluída com sucesso!"
