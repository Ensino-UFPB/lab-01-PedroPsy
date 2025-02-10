[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/zIWE17F2)
# Gerência de Redes de Computadores
Lab 01 - Ferramentas Básicas

# Aula: Utilitários de Rede no Windows e Linux

Nesta aula, você aprenderá a utilizar alguns utilitários que podem ajudá-lo a gerenciar uma rede de computadores. O funcionamento dessas ferramentas e os conceitos envolvidos são a base para o **Gerenciamento de Redes de Computadores**.

## Utilitários abordados na aula:
- `route`
- `ip`
- `nslookup`
- `ping`
- `traceroute`
- `netstat`
- `telnet`
- `mtr`


# Instruções para executar o container do lab e acessá-lo

### **1. Iniciando o ambiente**
Para iniciar o ambiente, rode:

```sh
docker-compose up -d
```

### **2. Acessando o ambiente**
Caso o container tenha sido iniciado com sucesso, você pode acessá-lo com o comando abaixo:

```sh
docker exec -it lab01 bash
```
A partir desse ponto você estará dentro de um ambiente linux com as ferramentas utilitárias necessárias para as práticas instaladas.

### **3. Desligando o ambiente**
Ao final do lab, quando você já tiver coletado todas as suas respostas, remova o container

```sh
docker-compose down
```

# Instruções e Questões 

Responda as questões em uma arquivo chamado `respostas.txt` que se encontra na raíz do projeto clonado via git. Para cada questão coloque o número da questão e abaixo sua resposta. Algumas questões você irá copiar a saída do terminal, para outras você irá responder de forma livre.


## **Questão 1. route**
O utilitário `route` é usado para listar, adicionar e remover regras da tabela de roteamento de um computador. Esta tabela é sempre consultada pela camada de rede do protocolo IP para determinar o próximo salto (*hop*) de um pacote.

### **Prática**
Utilize o comando `route -n` para verificar a tabela de roteamento e responder:
1. **Qual a sua rede e máscara?**
2. **Qual o seu roteador padrão (*default gateway*)?**
3. **Quantas rotas configuradas tem seu computador?**
---

## **Questão 2. ip (ipconfig/ifconfig)**
O comando `ip` exibe detalhes de todas as interfaces de rede disponíveis no computador.

### **Prática**
Utilize o comando `ip a` para verificar as questões abaixo:
1. **Qual o IP da interface de rede?**
2. **Qual a rede e a máscara?**
4. **Qual o nome da interface de rede principal?**

---

## **Questão 3. nslookup **
O `nslookup` é usado para traduzir nomes de domínio para seus respectivos endereços IP, consultando servidores DNS.

### **Prática**
Descubra o endereço IP dos seguintes domínios e informe no arquivo de respostas:
```sh
nslookup www.google.com
nslookup www.whitehouse.gov
nslookup www.rnp.br
nslookup www.ufpb.br
```
---

## **Questão 4. ping**
O utilitário `ping` testa a conectividade entre duas máquinas, enviando pacotes ICMP e aguardando resposta.

### **Prática**
1. **Teste a conectividade da sua rede local**:
   - Pingue a interface de loopback: `ping 127.0.0.1`. Qual o tempo de resposta?
   - Pingue seu próprio endereço IP dentro do container. Qual o tempo de resposta?

2. **Teste a conectividade com a Internet**:
   - `ping www.ufpb.br`
   - `ping www.yahoo.com`
   - `ping www.brasil.gov.br`
   - `ping www.dce.ufpb.br`

   Quais os tempos de resposta para cada um dos sites. Algum estava inacessível, qual mensagem apareceu?


3. **Analise os tempos de resposta**:
   - Compare os tempos de resposta para diferentes sites:
     - `ping www.google.com`
     - `ping www.rnp.br`
     - `ping www.whitehouse.gov`
   - O que pode influenciar as diferenças nos tempos?
---

## **Questão 5. traceroute**
O `traceroute` mostra por onde um pacote IP trafega até chegar ao destino. Ele ajuda a identificar onde uma comunicação pode estar congestionada ou interrompida.

### **Prática**
1. Execute `traceroute`nos seguintes domínios:
   ```sh
   traceroute www.google.com
   traceroute www.rnp.br
   traceroute www.whitehouse.gov
   ```
   - Por que alguns roteadores ao longo do caminho não respondem?
   - Isso significa necessariamente que há um problema na rede?

---

## **Questão 6. netstat**
O `netstat` exibe as conexões ativas na máquina, mostrando protocolos, portas e status das conexões.

### **Prática**
1. Liste todas as conexões e portas de escuta:
   ```sh
   netstat -tulnp  # Linux
   ```
2. Mostre a tabela de roteamento:
   ```sh
   netstat -r
   ```
   - Os resultados são os mesmos do comando `route`?
   - Há informações adicionais?

---

## **Questão 7. telnet**
O `telnet` permite testar a conectividade de um serviço em uma porta específica.

### **Prática**
1. Teste a conectividade do servidor web na porta 80:
   ```sh
   telnet www.ufpb.br 80
   ```
   - O servidor respondeu? O serviço está ativo?

2. Teste a conectividade do serviço FTP na porta 21:
   ```sh
   telnet www.dce.ufpb.br 21
   ```
   - Você conseguiu conexão? Se não, como diferenciar um problema de rede de um problema no serviço?

---

## **Questão 8. mtr**
O `mtr` combina as funções do `ping` e `traceroute`, monitorando a rota e latência dos pacotes em tempo real.

### **Prática**
1. Pesquise sobre o utilitário `mtr`.
2. **Explique em que situações ele pode ser útil** no gerenciamento de redes.
3. Teste `mtr` com alguns domínios:
   ```sh
   mtr www.google.com
   mtr www.ufpb.br
   ```
4. **Pesquisa como interpretar os resultados deste utilitário e explique como esses dados podem ajudar a diagnosticar problemas na rede.**

---

# Finalizando a prática

Verifique se toda as suas respostas estão salvas no arquivo resposta.txt na raíz do projeto clonado. 
Faça o commit e push do arquivo de resposta no repositório do laboratório

## **Conclusão**
Nesta aula, você aprendeu a utilizar diversos comandos fundamentais para o gerenciamento e diagnóstico de redes, tanto no Windows quanto no Linux. Experimente combinar diferentes ferramentas para obter diagnósticos mais completos e melhorar sua compreensão sobre redes de computadores!

🔹 **Dica:** Teste os comandos regularmente para se familiarizar com seu uso e aplicação prática. 🚀
