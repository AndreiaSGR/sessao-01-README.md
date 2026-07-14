# sessao-01-README.md
Exercícios Sessão Linux e Cyber Segurança
### `ip a` <img width="948" height="595" alt="Captura de ecrã 2026-07-14 200003" src="https://github.com/user-attachments/assets/c164ab95-f8af-4216-8356-f1259d93e44b" /> 
### `ss -tuln`<img width="947" height="964" alt="Captura de ecrã 2026-07-14 200055" src="https://github.com/user-attachments/assets/8b9f5a9d-b254-4865-85c7-b3cfa348c38a" />
## Scan Nmap ao alvo (TryHackMe)Comando usado: nmap -sV -sC <IP_DO_ALVO> <img width="1412" height="561" alt="image" src="https://github.com/user-attachments/assets/74d1f47f-f1ed-4b0c-8ff7-4f2af30128d5" />2.2 Riscos identificados
SSH (22/tcp) — OpenSSH 9.6p1: versão atual, sem vulnerabilidades críticas conhecidas à data. Ainda assim, é um alvo natural para ataques de força bruta se a autenticação por password estiver ativa.
DNS (53/tcp) — dnsmasq 2.90: serviço DNS exposto pode ser usado para reconhecimento adicional da rede ou, em cenários de má configuração, para ataques de amplificação DNS.
SMB (139/445/tcp) — Samba 4.6.2: o risco mais significativo do scan. O script `smb2-security-mode` reportou "Message signing enabled but not required", o que expõe o alvo a ataques de SMB relay, já que a assinatura de mensagens não é obrigatória.
Amazon DCV (8443/tcp): serviço de acesso remoto a desktop (comum em ambientes AWS). Certificado SSL válido até 2027-02-16. A exposição de serviços de desktop remoto deve ser sempre monitorizada quanto a tentativas de acesso não autorizado.
Portas filtradas (7777, 7778): presença de firewall a filtrar tráfego para estas portas — não foi possível confirmar se estão realmente ativas.

<img width="1885" height="941" alt="Captura de ecrã 2026-07-14 201939" src="https://github.com/user-attachments/assets/4c952a6a-af3f-491e-93b6-bbc2fa12c868" /><img width="1919" height="982" alt="Captura de ecrã 2026-07-14 202012" src="https://github.com/user-attachments/assets/85e15c1b-bd4d-45a4-9329-c47c55756eb7" />

## Conclusões
O scan identificou 5 portas abertas confirmadas (22, 53, 139, 445, 8443) e 2 portas filtradas (7777, 7778) num alvo Linux. O maior risco encontrado foi o serviço Samba (SMB) nas portas 139/445, que tem a assinatura de mensagens ativa mas não obrigatória, tornando o alvo potencialmente vulnerável a ataques de SMB relay. Recomenda-se também rever a exposição do DNS (dnsmasq) e do serviço Amazon DCV na porta 8443, que permite acesso remoto ao desktop
