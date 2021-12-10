<h1 align="center">
  Desafio SAS - Gerenciador de Simulados
  <br>
</h1>

<!-- <h4 align="center"></h4> -->

<p align="center">
    <a alt="Java">
        <img src="https://img.shields.io/badge/Java-v11-orange.svg" />
    </a>
    <a alt="Spring Boot">
        <img src="https://img.shields.io/badge/Spring%20Boot-v2.5.6-brightgreen.svg" />
    </a>
    <a alt="Flyway">
        <img src="https://img.shields.io/badge/Flyway-v8.0.4-brown.svg">
    </a>
    <a alt="Swagger-UI">
        <img src="https://img.shields.io/badge/SwaggerUI-v2.9.2-green.svg">
    </a>    
</p>

## Índice ##
1. [Descrição do desafio](#Descrição-desafio)
2. [Tecnologias](#Tecnologias)
3. [Diagramas UML](#Diagramas-UML)
4. [Esquema Banco de Dados](#Esquema-Banco-de-Dados)
5. [Requisitos](#Requisitos)
6. [Instruções de uso](#Instruções-de-uso)
7. [Documentação REST](#Documentação-REST)


## Descrição do desafio ##

O SAS Aplica periodicamente simulados em toda a base de escolas para medir o desempenho de seus alunos. Para isso, precisamos de um sistema que faça a gestão desses simulados.

### Regras de negócio: ###

* Um simulado poderá ter N provas
* Cada prova tem uma lista de 10 questões, sendo 3 fáceis, 4 médias e 3 difíceis
* Cada prova contém um gabarito diferente associado

#### Cálculo de nota: ####
As notas dos alunos será composta pela seguinte formula:
$$
NP = (Qf *Vf) + (Qm *Vm) +  (Qd *Vd) + 600
$$
Onde,
*NP*: Nota da prova
*Qf*: quantidade de acertos de questões fáceis
*Qm*: quantidade de acertos de questões médias
*Qd*: quantidade de acertos de questões difíceis
*Vf*: valor de uma questão fácil.
*Vm*: valor de uma questão média.
*Vd*: valor de uma questão difícil.

|     Nível      |      Valor     |
|----------------|----------------|
|Fácil           |`15 pontos`     |
|Média           |`12 pontos`     |
|Difícil         |`8 pontos`      |

**A nota final do aluno será a média das notas de todas as provas de um simulado.**

#### Empate: ####
Caso haja empate de notas, os alunos que tiverem a mesma nota deverão ter a mesma classificação, por exemplo:

|     Aluno      |      Nota      |     Ranking    |
|----------------|----------------|----------------|
|João            |`750`           |`1`             |
|Pedro           |**`690`**       |**`2`**         |
|Maria           |**`690`**       |**`2`**         |
|Antonio         |`500`           |`4`             |
|José            |`400`           |`5`             |

### API: ###
Gostaríamos que fossem implementados os seguintes endpoints:

* Listagem de simulados
* Listagem do gabarito de uma prova
* Responder questão
* Listagem do Ranking dos 5 alunos melhores colocados com suas respectivas notas em um simulado

**Você poderá criar uma migration para ter uma massa de respostas.**

## O que iremos avaliar ##

* Se as funcionalidades estão implementadas corretamente
* Padrão REST
* Testes unitários
* Design de código (SOLID, DRY, KISS)
* Arquitetura da solução
* Documentação

## Pontos extras ##

* Ambiente rodando em container
* Uso de migrations para criação do banco de dados
* Hospedagem em alguma nuvem pública



## Tecnologias ##
Following libraries were used during the development of this starter kit :

- **Maven** - Software de gerenciamento de projetos
- **Spring Boot** - Framework de aplicações Java
- **PostgreSQL** - Banco de dados SQL
- **Flyway** - Framework de migrations 
- **Docker** - Framework de conteinerização
- **Swagger** - Documentação de API


### Diagrama de Caso de Uso ###

<img src="./docs/images/DesafioCasoDeUso.drawio.png" alt="caso_de_uso"></a>

### Diagrama de Classes ###

<img src="./docs/images/DesafioClasse.drawio.png" alt="classes"></a>


## Esquema Banco de Dados ##

<img src="./docs/images/DesafioEntidadeRelacionamento.drawio.png" alt="db_esquema"></a>

  

## Instruções de uso ##

**1. Clonar repositório**

**2. Criar banco de dados PostgreSQL**
```bash
CREATE DATABASE desafiosas;
```

**3. Configurar username e password do postgres no properties**

+ Caminho: `src/main/resources/application.properties`

**4. Build e start usando maven**

```bash
./mvnw clean && ./mvnw package
java -jar target/desafio-0.0.1-SNAPSHOT.jar
```

Aplicação estará disponível em <http://localhost:8080>.

## Documentação REST ##

Os recursos REST da api estão documentados com Swagger, disponíveis uma vez que o projeto esteja rodando: [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)

<img src="./docs/images/swagger-ui.png" alt="swagger-ui"></a>
  

## Contribuidores ##
[Lucas Tavares](https://www.linkedin.com/in/lucas-tavares-a25323116/)
