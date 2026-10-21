# Laboratório 01 - Diagnóstico básico de rede

## Objetivo

Realizar testes básicos de diagnóstico de rede no Windows utilizando os comandos `ipconfig`, `ping`, `nslookup` e `tracert`, identificando a configuração da rede local, testando a conectividade e observando a resolução de nomes e o caminho até um destino.

## 1. Verificando a configuração da rede com `ipconfig`

O primeiro comando utilizado foi:

`ipconfig`

Esse comando permite visualizar informações da configuração de rede do computador, como endereço IPv4, máscara de sub-rede e gateway padrão.
Durante o teste, identifiquei essas informações na configuração do adaptador de rede utilizado.
Por segurança e privacidade, os valores específicos da minha rede local não foram publicados neste repositório.

### O que identifiquei

- **Endereço IPv4:** identifica o dispositivo dentro da rede local.
- **Máscara de sub-rede:** ajuda a determinar qual parte do endereço identifica a rede e qual parte identifica os dispositivos.
- **Gateway padrão:** endereço utilizado pelo dispositivo para alcançar outras redes.

## 2. Testando a comunicação com o gateway

Depois de identificar o gateway padrão da rede, utilizei o comando `ping` para verificar se o computador conseguia se comunicar com ele.
O comando utilizado foi:

`ping [gateway]`

O teste enviou 4 pacotes e todos foram recebidos, sem perda de pacotes.

### Resultado

- **Pacotes enviados:** 4
- **Pacotes recebidos:** 4
- **Pacotes perdidos:** 0
- **Perda:** 0%

O resultado mostrou que havia comunicação entre o computador e o gateway da rede local.
O comando `ping` utiliza o protocolo ICMP para testar a comunicação entre dispositivos e também apresenta informações como o tempo de resposta.

## 3. Testando a conectividade com um endereço externo

Em seguida, utilizei o comando `ping` com o endereço `8.8.8.8`, que pertence ao serviço Google Public DNS.
O comando utilizado foi:

`ping 8.8.8.8`

Diferente do teste anterior, que verificou a comunicação dentro da rede local com o gateway, este teste foi utilizado para verificar se o computador conseguia alcançar um endereço IP externo.

### Resultado

- **Pacotes enviados:** 4
- **Pacotes recebidos:** 4
- **Pacotes perdidos:** 0
- **Perda:** 0%

O resultado mostrou que havia conectividade com uma rede externa.

## 4. Testando a conectividade com um nome de domínio

Depois do teste com um endereço IP, utilizei o comando `ping` com um nome de domínio:

`ping google.com`

Nesse caso, antes de realizar o teste de comunicação, o computador precisou descobrir qual endereço IP estava associado ao domínio `google.com`.
O teste foi concluído sem perda de pacotes, mostrando que o domínio foi resolvido e que houve comunicação com o destino.

### Diferença observada

- `ping 8.8.8.8` → utiliza diretamente um endereço IP.
- `ping google.com` → utiliza um nome de domínio, que precisa ser resolvido para um endereço IP.

Esse teste ajudou a entender a relação entre nomes de domínio e endereços IP.

## 5. Consultando o DNS com `nslookup`

Para consultar diretamente a resolução de nomes, utilizei o comando:

`nslookup google.com`

O comando mostrou o servidor DNS responsável por responder à consulta e os endereços associados ao domínio pesquisado.
No resultado, foram apresentados endereços nos formatos IPv4 e IPv6.

### O que aprendi

O DNS (Domain Name System) permite relacionar nomes de domínio a endereços IP.
De forma simplificada: `google.com` → DNS → endereço IP

Isso permite que os usuários utilizem nomes de domínio em vez de precisar memorizar os endereços IP dos serviços.
O `nslookup` pode ser utilizado para consultar informações de DNS e auxiliar na identificação de problemas relacionados à resolução de nomes.

## 6. Rastreando a rota com `tracert`

Por último, utilizei o comando:

`tracert google.com`

Esse comando permite observar o caminho percorrido pelos pacotes até chegar ao destino.
Durante o teste, foram apresentados diferentes saltos (hops). Cada salto representa a passagem por um equipamento de rede ao longo do caminho até o destino.
O primeiro salto correspondeu ao gateway da minha rede local. Depois, o tráfego passou por outros equipamentos até chegar ao destino.

### O que aprendi

O `tracert` ajuda a visualizar o caminho percorrido até um destino e pode auxiliar na identificação de pontos em que podem estar ocorrendo problemas de comunicação.
O tempo apresentado em milissegundos (`ms`) indica o tempo de resposta observado em cada salto.

## Conclusão

Neste laboratório pratiquei alguns comandos básicos de diagnóstico de rede no Windows.
Com o `ipconfig`, identifiquei informações da configuração da rede local. Com o `ping`, testei a comunicação com o gateway e com destinos externos. O `nslookup` permitiu consultar a resolução de nomes por DNS, enquanto o `tracert` mostrou os saltos realizados até chegar a um destino.

A prática me ajudou a entender melhor como verificar a conectividade de um computador e como esses comandos podem ser utilizados para identificar possíveis problemas de rede.