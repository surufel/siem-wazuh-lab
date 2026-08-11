# Laboratório SIEM com Wazuh

Eu organizei um laboratório de SIEM usando o Wazuh. Para isso, usei duas máquinas virtuais:

- Ubuntu: hospedando o Wazuh (manager);
- Windows 10: atuando como agente;

O propósito desse laboratório é obter experiência prática com ferramentas de SIEM no geral. Desde a instalação até a análise de eventos de segurança, buscando entender detalhadamente as vulnerabilidades.

---

## Máquinas Virtuais usadas no processo:

_VM do Ubuntu com seu IP:_
<figure>
  <img src="docs/ubuntu_ip.png" width="600">
</figure>

_VM do Windows com seu IP:_
<figure>
  <img src="docs/windows_ip.png" width="600">
</figure>

---

## Investigação

Assim que criei a máquina virtual do Ubuntu e instalei por meio do Quickstart na documentação do Wazuh, configurei um novo agente, que é a segunda máquina virtual usada no laboratório.
A seguir, o dashboard do endpoint.

![Dashboard do Endpoint (VM do Windows 10)](docs/windows-agent.png)

Podemos perceber que há varias detecções de vulnerabilidades. Mas veremos primeiramente algo que o Wazuh cuidou de fazer como primeira instância, o scan do CIS Benchmark:

![CIS Benchmark](docs/cis-benchmark.png)

Nota-se que o scanning do CIS benchmark revelou que o agente possui um score aproximado de 25%.
Esse score está medindo a porcentagem de compliance que o endpoint teve.
É categórico que a instalação padrão do Windows não é suficiente para segurança.
Até mesmo nas versões atuais do Windows, pode ser descoberto vulnerabilidades em um sistema mal protegido.

Agora, iremos para a seção de Vulnerability Detection. De todas as 21 vulnerabilidades críticas, temos como as 5 maiores vulnerabilidades:

![Vulnerability Detection](docs/vulnerability-detection.png)

**As 5 maiores vulnerabilidades listadas pela Detecção de Vulnerabilidades são:**

- CVE-2024-38063
- CVE-2024-38140
- CVE-2024-38199
- CVE-2025-21298
- CVE-2025-21307
