Quagga Routing
==============
Ansible Role para instalar e configurar Quagga Routing Suite.  

Os arquivos de configuração base estão no diretório templates e devem ser copiados para o ambiente de execução, as configurações dos protocolos de roteamento devem ser realizadas nos respectivos arquivos.  

Os protocolos ativos neste role são BGP e OSPF.  

Arquivos:  
> router_zebra.conf.j2  
> router_vtysh.conf.j2  
> router_bgpd.conf.j2  
> router_ospfd.conf.j2  

Requisitos
----------
Debian 9  

Variáveis do Role
-----------------
Nome do roteador:
```yaml
quagga_hostname: "router_01" 
```

Arquivo de log:
```yaml
quagga_logfile: "/var/log/zebra.log"
```

Senha de acesso:
```yaml
quagga_password: "zebra"
```

Arquivo de configuração zebra.conf:
```yaml
quagga_zebra_conf_file: "../env_data/quagga/router01_zebra.conf.j2"
```

Arquivo de configuração vtysh.conf:
```yaml
quagga_vtysh_conf_file: "../env_data/quagga/router01_vtysh.conf.j2"
```

Arquivo de configuração bgpd.conf:
```yaml
quagga_bgpd_conf_file: "../env_data/quagga/router01_bgpd.conf.j2"
```

Arquivo de configuração ospfd.conf:
```yaml
quagga_ospfd_conf_file: "../env_data/quagga/router01_ospfd.conf.j2"
```

Dependências
------------

Nenhuma.

Playbook de exemplo
-------------------
```yaml
---
- name: Instala o quagga
  hosts: quagga-router
  become: true
  gather_facts: true

  roles:
    - role: ansible-role-quagga
      quagga_hostname: "router01"
      quagga_logfile: "/var/log/zebra.log"
      quagga_password: "zebra"
      quagga_zebra_conf_file: "../env_data/quagga/router01_zebra.conf.j2"
      quagga_vtysh_conf_file: "../env_data/quagga/router01_vtysh.conf.j2"
      quagga_bgpd_conf_file: "../env_data/quagga/router01_bgpd.conf.j2"
      quagga_ospfd_conf_file: "../env_data/quagga/router01_ospfd.conf.j2"
```

Licença
-------

MIT

Informações do Autor
--------------------

Fabricio Boreli  
fabricioboreli at openmailbox dot org
