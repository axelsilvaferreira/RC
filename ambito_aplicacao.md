Âmbito de Aplicação
===================

Desde o streaming de vídeo de alta qualidade, às aplicações online de 
tempo real, o modo básico de funcionamento das CDNs é idêntico. Ao 
invés da típica relação binária entre cliente-servidor, o modelo 
proposto pelas CDNs foca-se na partilha dos vários recursos entre 
servidores para garantir ao utilizador um acesso mais rápido e
eficiente dos conteúdos.

Deste modo, numa típica aplicação de uma CDN, relacionar-se-ão três
entidades distintas:
 * Um **provedor de conteúdos**, responsável pela gestão e criação dos
   mesmos.
 * Uma **rede de servidores "substitutos"** ~~(surrogate?)~~ com conteúdo
   replicado do provedor de conteúdos, espalhados geograficamente
   por diversos locais do mundo.
 * Um conjunto de **utilizadores** distintos, receptores de conteúdos.

Este modelo, actualmente pode ser implementado de duas maneiras
distintas, através de uma **arquitectura comercial** ou de uma 
**arquitectura académica**.

~~??Explicar arquitecturas??~~

## Arquitectura comercial
As arquitecturas comerciais são as que seguem mais fielmente o modelo
anteriormente descrito. Normalmente uma empresa é responsável pela 
manutenção dos servidores substitutos, bem como pelo seu aluguer. O
dono do website deve pagar o preço de aluguer dos servidores e 
escolher que conteúdo pretende ser replicado.

Por exemplo, suponhamos uma página de notícias online, que para além 
de texto escrito possui diversos vídeos com reportagens. Numa 
aplicação comercial típica de CDN, o gestor do site, incorporaria no 
código fonte HTML da página, links para servidores alugados que 
possuíam os conteúdos mais pesados (os vídeos das reportagens).
Deste modo, o utilizador quando acedesse ao site obteria um 
carregamento muito mais rápido do mesmo, pois ao mesmo tempo que o 
texto era carregado directamente do provedor de conteúdos, os vídeos 
seriam carregados a partir dos servidores da empresa. 


## Arquitectura académica
Contrariamente ao modelo comercial, as arquitecturas académicas
tratam-se de modelos `peer-to-peer` sem fins lucrativos, onde cada 
utilizador partilha um pouco dos recursos da sua máquina (memória, 
ciclos de CPU, etc...) com os restantes intervenientes.
Esta alternativa torna a rede independente de servidores empresariais,
o que faz com que a mesma se torne bastante barata (o preço a pagar
são os pequenos recursos partilhados). Outra vantagem desta
arquitectura advém de a qualidade e velocidade da rede aumentar em
proporção do número de utilizadores da mesma, i.e, quantos mais
utilizadores tiver a rede, mais rápida e fiável é a mesma.

Por exemplo, um `streaming` de alta qualidade para um número elevado
de utilizadores pode ganhar vantagens em utilizar uma arquitectura
académica, já que o provedor desse mesmo `streaming` não teria que
lidar com os custos de aluguer de servidor e, para além disso, o
elevado número de utilizadores garantiria um maior leque de recursos
disponíveis para a transmissão do vídeo globalmente.


# Provedor de conteúdos

O provedor de conteúdos pode tratar-se de um servidor normal, no qual 
estão alojados os conteúdos que se pretendem partilhar (páginas HTML, 
imagens, vídeos, aplicações flash, etc ...), ou de um computador
pessoal no caso de se tratar de uma arquitectura académica.


# Servidores "substitutos"

Os servidores "substitutos" funcionam como um mecanismo de redundância
dos dados existentes nos provedores de conteúdo. Estes formam uma rede
entre si, podendo um servidor estar ligado a outros tantos, bem como 
ao próprio provedor de conteúdos. Esta característica particular 
garante acessos muito mais rápidos aos dados, pois quando um 
utilizador acede a um website que faça uso de uma CDN, é 
automaticamente redirecionado para o servidor que lhe é mais 
apropriado (sendo esta escolha efectuada através de um algoritmo
baseado nas características da rede, proximidade entre servidor e
cliente, entre outros...).

~~[Imagem de uma rede de servidores "surrogate"]~~

## Sincronização entre servidores

É importante notar que uma vez que o conteúdo se encontra disperso por
vários locais distintos, é imperativa a existência de uma 
sincronização eficiente e segura entre eles. Para tal, recorre-se a 
técnicas de sincronização automática, que de uma forma simplista, 
funcionam da seguinte maneira:

 1. O provedor de conteúdos altera ou insere novos conteúdos na página
 2. Os servidores mais próximos são actualizados imediatamente, e 
    estes por sua vez actualizam outros servidores próximos de si
 3. O passo anterior é repetido várias vezes até que todos os 
    servidores da rede possuam os mesmos conteúdos


# Principais vantagens

Dá para entender que, dadas as suas características, as CDN revelam-se
bastante úteis no panorama actual da computação online, onde são
exigidas enormes transferências de dados, segurança e estabilidade dos
mesmos. Assim sendo, é possível concluir que as CDN apresentam-se como
uma alternativa fiável e robusta ao paradigma tradicional de acesso à
informação, pois:

 * garantem **redundância dos dados**, já que estes encontram-se
   replicados por diversos servidores espalhados na rede, o que
   garante uma maior facilidade de restauro no caso de perda de algum
   servidor (por exemplo, se um servidor avaria, os dados podem ser
   recuperados a partir de outro servidor);

 * são **mais resistentes** a ataques de "bruta força" (tais como 
   `DDos`~~[breve descrição sobre DDos?]~~), pois o tráfego excessivo
   produzido por estes ataques pode ser canalizado para os servidores
   substitutos, reduzindo substancialmente a carga de cada um;

 * garantem um **baixa latência** de comunicação entre cliente e 
   servidor, pois o cliente acede ao servidor que lhe é mais próximo, 
   o que diminui a distância que a informação tem de percorrer;

 * reduzem consideravelmente os problemas de `unpredictable bursting`
   (um evento ocorre e estimula a utilização excessiva dos recursos) e
   de `predictable bursting` (é esperado que de tempos a tempos haja
   um pico de acesso ao(s) servidor(es)), dado que quando estes 
   ocorrem o tráfego excessivo é distribuído pelos vários servidores, 
   não ficando apenas um único servidor sobrecarregado.
