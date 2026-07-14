# sessao-01-README.md
Exercícios Sessão Linux e Cyber Segurança
### `ip a` <img width="948" height="595" alt="Captura de ecrã 2026-07-14 200003" src="https://github.com/user-attachments/assets/c164ab95-f8af-4216-8356-f1259d93e44b" /> 
### `ss -tuln`<img width="947" height="964" alt="Captura de ecrã 2026-07-14 200055" src="https://github.com/user-attachments/assets/8b9f5a9d-b254-4865-85c7-b3cfa348c38a" />
## Scan Nmap ao alvo (TryHackMe)Comando usado: nmap -sV -sC <IP_DO_ALVO><img width="1885" height="941" alt="Captura de ecrã 2026-07-14 201939" src="https://github.com/user-attachments/assets/4c952a6a-af3f-491e-93b6-bbc2fa12c868" />
## Conclusões
O scan identificou 5 portas abertas confirmadas (22, 53, 139, 445, 8443) e 2 portas filtradas (7777, 7778) num alvo Linux. O maior risco encontrado foi o serviço Samba (SMB) nas portas 139/445, que tem a assinatura de mensagens ativa mas não obrigatória, tornando o alvo potencialmente vulnerável a ataques de SMB relay. Recomenda-se também rever a exposição do DNS (dnsmasq) e do serviço Amazon DCV na porta 8443, que permite acesso remoto ao desktop
