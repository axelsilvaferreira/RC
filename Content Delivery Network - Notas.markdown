Content Delivey Networks
========================

# O que são?


# Vantagens


# Desvantagens


# Tipos de CDN

Principal fonte:
[An Architecture for Distributed Content Delivery Network](http://ieeexplore.ieee.org/xpls/icp.jsp?arnumber=4444113)

Existem dois tipos principais de CDN actualmente em utilização, com 
diferentes arquitecturas:

## Arquitectura comercial
 - Relação cliente-servidor quase exclusiva
 - Ver exemplo da Akami
 - *Modo de funcionamento* - os clientes (provedores de conteúdo) 
 alugam a sua quota de armazenamento nos servidores da Akamai. A sua 
 aplicação, passa então a estar distribuída por mais de 20 000 
 ervidores da Akamai, o que permite um melhor desempenho da mesma 
 (ver secção `Vantagens`). O seu modo de utilização é o seguinte:

   1. O browser do utilizador acede à aplicação normalmente (através do
   da página `index.html`, como em todos os sites)
   2. O código `HTML` da aplicação possui links para conteúdos (imagens,
   videos, jogos, etc...) armazenados nos servidores da Akamai
   3. O browser do utilizador processa o código `HTML` ao mesmo tempo
   que obtém os conteúdos dos servidores da Akamai, resultando num 
   aumento da performance do mesmo.

**Principal desvantagem** - custo financeiro de aluguer dos servidores
muito elevado (só grandes empresas conseguem pagá-lo). Sendo a Akamai a
principal empresa desta área, este serviço torna-se monopolizado, ~~o que
retira o poder de escolha aos clientes, e garante à Akamai poder absoluto
sobre o serviço (i.e., a Akamai controla os preços conforme quiser pq
não possui concorreência)~~





## Arquitectura académica

Está também prevista a criação de uma nova arquitectura, 
**Distributed Content Delivery Network**, que cobre as vantagens dos 
dois anteriores, sem estar sujeita às desvantagens dos mesmos


# Cenários de utilização
