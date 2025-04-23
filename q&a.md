# Perguntas e Respostas

## 1ª Semana

### Devemos ter um PC por serviço na DMZ?

Sim, porque assim podemos ter regras diferentes para cada um dos serviços

### Devemos ter várias VLANs na DMZ? Uma para cada serviço?

Devíamos ter, mas não vale a pena.

### Devemos minimizar as subredes (ter o menor número de IPs possíveis) ou podemos usar todos os IPs disponíveis?

Podemos colocar /24

### Quantos endereços IP para o NAT? Qual é a gama de endereços públicos?

É só escolher à toa.

### É preciso um router para a Internet (agora o PC não tem gateway)? Que rede usar entre este router e os routers de saída?

Não, a gateway do PC da internet é o IP da FW Stateless.

## 2ª semana

### Temos o NAT nos routers de saída, não seria melhor nas firewalls stateful do core?

É subjetivo, mas não tem problema porque fizemos NAT stateful.

### Tráfego do Datacenter tmb tem de ir à FW?

Não era necessário, mas não faz mal.

### OSPF tem de ser configurado para as redes intermédias (router a router)? Pode/Deve ser redistribuido para não ter tabelas gigantes?

Sim, tem de ser configurado para as redes intermédias. Não deve ser redistribuído porque não é necessário.

### Em relação à security policy nº 1 do enunciado, como é que é suposto aguentar ataques de DDoS? É criar um script como estava no guião?

Bloquear nas FW's Stateless com base em gamas de IP. Podemos ir buscar ao abuse.ch, por exemplo.

### A DMZ tem acesso à Internet (ou tem só established/related)?

Deve ter acesso à Internet para fazer updates, logo só deve ter acesso a serviços específicos. Fica a dúvida em que serviços, porque o projeto não tem nada que fale nisso.

### É preciso fazer mesmo SSH com o dispositivo do Admin ou é só preciso estabelecer regras para o porto 22 (2022 por causa dos pings TCP)?

Não, é só ter o porto aberto e conseguir pingar.

### O admin pode também pingar e fazer SSH para a Internet (passar das stateless para cima)?

Não, só até às stateless que são os últimos dispositivos da rede.
