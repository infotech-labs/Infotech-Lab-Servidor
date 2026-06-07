# Infotech-Lab-Servidor
Servidor Proxmox da INFOTECH

Infotech, é uma assistencia Tecnica em Caraguatatuba, onde presta serviços de manutenção em computadores e notebooks, impressoras, e venda de suprimentos para informática;

Projeto criado em um Servidor Lenovo TS140, onde foi instalado o software de virtualização PROXMOX 8.4.17 para eu poder aplicar todos os meus recursos necessários que auxiliam no dia-a-dia de trabalho dos profissionais da empresa.

PROXMOX VE 8.4.17
Windows 10 LTSC
Linux 
Debian 12
OwnCloud
OpenVPN
Samba
Node.js + CloudFlare

##Arquitetura da Rede:

INTERNET (Modem Claro com CGNAT Habilitado) - Portas especificas habilitadas apontando para o Roteador
           
                ||
   
    Roteador TP Link Archer C5 - Serviço NO-IP configurado para acesso externo e portas apontando para o servidor.
              
                ||
            
              PROXMOX
      |---(CT 101) Debian 12 com OwnCloud Configurado para enxergar os arquivos no Storage 3;
      |---(CT 200) Debian 12 com Node.Js rodando o template do website feito no replit.com + Cloudflare para apontar para meu                                servidor a hospedagem do site da loja;
      |---(CT 300) Debian 12 com Samba configurado para hospedar um NAS interno com os arquivos alojados no HOST  / ;
      |---(CT 400) Debian 12 configurado uma VPN com OpenVPN para acessos externos dos funcionarios;
      |---(VM 100) Windows LTSC para rodar o software de gerenciamento da assistencia chamado SHOficina com banco de dados MDB.

      A Assistencia tecnica possui outros 3 computadores que enxergam esse servidor e acessam os respectivos serviços NAS e o Servidor do SHOficina para compartilhar o banco de dados, e os demais serviços servem para dar auxilio geral, como o OwnCloud que é uma nuvem particular para os colaboradores poderem armazenar seus arquivos e programas, o OpenVPN para conexao segura a rede interna da empresa, e o site que fica hospedado no servidor com acesso pelo link https://web.infotechcaragua.net/ .

     Foram aplicados conceitos de criação de maquinas virtuais e containers, configuração de rede e administração de aplicativos em ambiente linux, como cloudflare, openvpn, owncloud, samba. Dentro do Proxmox foram feitos ajustes no gerenciamento do host, desabilitando o SSH na porta padrao, para evitar ataques, bem como restrição de acesso root ao Host via SSH. O Servidor Fisico possui 2 discos de 1 terabyte, sendo 1 para armazenamento de dados no HOST que servem o CT 300 e o outro aplicado como STORAGE 1 para back-up da VM e dos CTs, e 1 Disco de 500gb onde possui back-up do banco de dados do Owncloud, que é onde se hospeda os arquivos.

###HARDWARE - Lenovo TS140
Memória RAM 20GB DDR3 PC3L 1666Mhz
SSD 240GB - Rodando o Proxmox / Host
1x HD 1TB - Armazenando no HOST os arquivos do CT300 em /dados
1x HD 1TB - STORAGE 1 (Para BACK-UP DE VM E CT)
1x HD 500gb - STORAGE 3 para back-up do Banco de dados do Owncloud.


###TELA PRINCIPAL DO HOST####
<img width="1365" height="460" alt="PVE - HOST" src="https://github.com/user-attachments/assets/bc90c276-392c-4871-b385-eb95d7ee34f1" />

###TELA DO CONTAINER CT101 - OwnCloud #### ( Nuvem de arquivos privada da empresa )
<img width="873" height="460" alt="CT101 - Owncloud" src="https://github.com/user-attachments/assets/e7ba837b-caaa-42ce-bf29-2bae3c3d2a07" />

###TELA DO CONTAINER CT200 - WebServer #### (Site da Loja web.infotechcaragua.net ) 
<img width="876" height="460" alt="CT200 - Webserver" src="https://github.com/user-attachments/assets/00aceb01-1c62-427f-98d8-9fb1fd57be35" />

###TELA DO CONTAINER CT300 - NAS #### (Storage interno de arquivos da Assistencia Tecnica) 
<img width="883" height="460" alt="CT300 - NAS" src="https://github.com/user-attachments/assets/281a3196-d908-4058-b2a7-b45c2eb27d66" />

###TELA DO CONTAINER CT400 - OpenVPN #### (VPN da Empresa)
<img width="876" height="460" alt="CT400 - OpenVPN" src="https://github.com/user-attachments/assets/a9a372c6-7ed1-4b28-a925-23c1c9f5ba3d" />

####TELA DA VM101 - Windows LTSC #### (Windows mais enxuto apenas para todar o SHOficina e suas funcionalidades, e compartilhar a pasta na rede para acesso aos terminais que acessam o respectivo software)
<img width="879" height="460" alt="VM100 - WindowsLTSC (SHoficina)" src="https://github.com/user-attachments/assets/3006e0cb-4b62-46a7-90e1-2aa332bb8823" />

###STORAGE Local-LVM #### Onde hospeda os discos de todos os containers e vms deste servidor, no SSD para melhor desempenho e acesso;
<img width="1360" height="460" alt="STORAGE LOCAL-LVM" src="https://github.com/user-attachments/assets/d5a89771-de94-4627-845f-d3a0a32257c8" />

####TELA DO STORAGE 1 - BACK-UP DAS VMS e CTS ##### Back-up Programado no PROXMOX para todos os recursos
<img width="1364" height="460" alt="STORAGE 1" src="https://github.com/user-attachments/assets/14dd3f8f-2d83-4d14-b1ac-fa797d5ae2d0" />

####TELA DO STORAGE 3 - Banco de Dados do OWNCLOUD #### DISCO AUXILIAR, onde apenas armazena o banco de dados da aplicação do CT 101
<img width="1361" height="460" alt="STORAGE 3" src="https://github.com/user-attachments/assets/7690cd58-cc4c-40f4-8e5b-f77ddb508973" />










