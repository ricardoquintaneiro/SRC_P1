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

### (Opcional) Podemos sicronizar as definições das FW Stateless?

### Tráfego do Datacenter tmb tem de ir à FW?

### OSPF tem de ser configurado para as redes intermédias (router a router)?

### Não faz sentido ter um load balancer antes das FW Stateless?

### Em relação à security policy nº 1 do enunciado, como é que é suposto aguentar ataques de DDoS? É criar um script como estava no guião?

### A DMZ tem acesso à Internet (ou tem só established/related)?