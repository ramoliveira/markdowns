# Modelo OSI

## Camadas

|Nº da Camada|Camadas|No mundo real|Exemplos de Protocolos|
|:-:|:-|:-|:-|
|1|Física/Physical|Sinais, cabos e conectores|Não possui protocolos|
|2|Enlace de Dados/Data Link|Quadros (*Frames*), Endereços MAC (Media Access Control), Extended Unique Identifier (EUI-48, EUI-64), Switch|Data Link Control (DLC), Ethernet, Wi-Fi (IEEE 802.11)|
|3|Redes/Network|Pacotes (*Packets*), Endereço IP, Roteador|Internet Protocol (IP)|
|4|Transporte/Transport|Segmentos (*Segment*) TCP, Datagrama (*Datagram*) UDP|TCP (Transmission Control Protocol) e UDP (User Datagram Protocol)|
|5|Sessão/Session|Comunicação entre dispositivos|Network Basic Input/Output System (NetBIOS), Point-to-Point-Tunneling Protocol (PPTP), AppleTalk Session Protocol (ASP)|
|6|Apresentação/Presentation|Codificação de caracteres, encriptação de aplicação|Secure Sockets Layer (SSL), Transport Layer Security (TLS)|
|7|Aplicação/Application|O que você está vendo|Hypertext Transfer Protocol (HTTP), Domain Name Systems (DNS)|


## Raio-X

```
Frame 88 (2005 bytes on wire, 2005 bytes captured) // Camada Física
Ethernet II, Src: Dell_6f:06:f2 (00:21:70:6f:06:f2), Dst: Netgear_d4:bb:fe (00:09:5b:d4:bb:fe) // Camada de Enlace de Dados
Internet Protocol, Src: 192.168.0.8 (192.168.0.8), Dst: googlemail.l.google.com (77.14.247.19) // Camada de Rede
Transmission Control Protocol, Src Port: 18429 (18429), Dst Port: https (443), Seq: 6597, Ack: 31926, Len: 1951 // Camada de Transporte
Secure Socket Layer // Camadas de Sessão, Apresentação e Aplicação
```
> Trecho transcrito a partir do Wireshark.

### Linha a linha do Raio-X
* `Frame 88 (2005 bytes on wire, 2005 bytes captured)`

    Apesar de parecer estar associada à camada de Enlace de Dados, pela presença do `frame`. Na verdade, esta linha é associada a Camada Física.
    > Sinais elétricos.

* `Ethernet II, Src: Dell_6f:06:f2 (00:21:70:6f:06:f2), Dst: Netgear_d4:bb:fe (00:09:5b:d4:bb:fe)`

    Esta linha está associada à camada de Enlace de Dados. Isto ocorre pela presença de endereços MAC.
    > Quadros de informação Ethernet.

* `Internet Protocol, Src: 192.168.0.8 (192.168.0.8), Dst: googlemail.l.google.com (77.14.247.19)`

    Esta linha está associada à camada de Rede. Pode-se perceber isso devido a presença do protocolo IP.
    > Encapsulamento de IP. Endereço IP.

* `Transmission Control Protocol, Src Port: 18429 (18429), Dst Port: https (443), Seq: 6597, Ack: 31926, Len: 1951 `

    Esta linha está associada à camada de Transporte. A presença do protocolo TCP indica isso.
    > Encapsulamento de TCP. Portas TCP.

* `Secure Socket Layer`

    Esta linha está encapsulando três camadas: Sessão, Apresentação e Aplicação.
    > Sessão: União da apresentação para o transporte.
    > Apresentação: Encriptação SSL.
    > Aplicação: `https://mail.google.com`


## Links Associados

1. [Media Access Control (MAC) Address](./mac-address.md)
2. [Internet Protocol (IP)](./ip.md)
3. [TCP](./tcp.md)
4. [UDP](./udp.md)
5. [Roteador](./devices.md/#Roteador)
