# Guia Completo de Configuração de Projeto Backend Spring Boot

## Pré-requisitos
- Java Development Kit (JDK) 17 ou superior
- IDE recomendada: 
  - IntelliJ IDEA
  - Eclipse
  - Spring Tool Suite
- Maven ou Gradle
- Git

## Métodos de Criação do Projeto

### 1. Usando Spring Initializr (Recomendado)

#### Opção Online
1. Acesse: https://start.spring.io/
2. Configurações básicas:
   - Project: Maven ou Gradle
   - Language: Java
   - Spring Boot: Versão mais recente estável
   - Projeto: 
     - Group: com.sua-empresa
     - Artifact: nome-do-projeto
     - Name: NomeDoProjeto
     - Description: Descrição do projeto
     - Package name: com.sua-empresa.nomedoprojeto

#### Dependências Iniciais Recomendadas:
- Spring Web
- Spring Data JPA
- Validation
- Banco de Dados (escolha um):
  - H2 Database (desenvolvimento)
  - PostgreSQL Driver
  - MySQL Driver
- Spring Boot DevTools
- Lombok
- Spring Security (opcional)

### 2. Criação via IDE

#### IntelliJ IDEA
1. Criar novo projeto
2. Selecionar Spring Initializr
3. Seguir passos similar ao Spring Initializr online

#### Eclipse
1. File > New > Other
2. Spring Boot > Spring Starter Project
3. Preencher configurações

## Estrutura Básica do Projeto

```
projeto-backend/
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── empresa/
│   │   │           └── projeto/
│   │   │               ├── controller/
│   │   │               ├── service/
│   │   │               ├── repository/
│   │   │               ├── model/
│   │   │               └── config/
│   │   │
│   │   └── resources/
│   │       ├── application.properties
│   │       └── application.yml
│   │
│   └── test/
│       └── java/
│           └── com/
│               └── empresa/
│                   └── projeto/
│
├── pom.xml (Maven)
├── build.gradle (Gradle)
└── README.md
```

## Configuração do Arquivo Principal

Arquivo `CuidaEmpregoApplication.java`:

```java
package com.exemplo.cuidaemprego;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class CuidaEmpregoApplication {

    public static void main(String[] args) {
        SpringApplication.run(CuidaEmpregoApplication.class, args);
    }
}
```

### Anotações Importantes

- `@SpringBootApplication`: Combina três anotações
  - `@Configuration`: Define classe de configuração
  - `@EnableAutoConfiguration`: Habilita configuração automática
  - `@ComponentScan`: Escaneia componentes no pacote atual

## Configuração de Banco de Dados

Exemplo `application.properties`:

```properties
# Configurações do Banco de Dados
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect

# Habilitar console H2
spring.h2.console.enabled=true

# Configurações JPA
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Porta do servidor
server.port=8080
```

## Dependências no Maven (pom.xml)

```xml
<dependencies>
    <!-- Spring Web -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!-- Spring Data JPA -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>

    <!-- Validação -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-validation</artifactId>
    </dependency>

    <!-- Banco de Dados H2 -->
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <scope>runtime</scope>
    </dependency>

    <!-- Lombok -->
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <optional>true</optional>
    </dependency>

    <!-- Testes -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```

## Comandos Úteis

```bash
# Compilar projeto
./mvnw clean install

# Rodar aplicação
./mvnw spring-boot:run

# Gerar build
./mvnw package

# Rodar testes
./mvnw test
```

## Padrões e Boas Práticas

1. Use injeção de dependência
2. Separe responsabilidades (MVC)
3. Use DTOs para transferência de dados
4. Implemente tratamento de exceções
5. Faça validações no modelo
6. Use logs para rastreabilidade

## Próximos Passos

- Configurar segurança
- Implementar autenticação
- Criar endpoints REST
- Configurar banco de dados de produção
- Implementar testes unitários e de integração

## Links Úteis

- Documentação Spring Boot: https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/
- Spring Initializr: https://start.spring.io/
- Guia de Referência: https://spring.io/guides
```

Explico os pontos principais:

1. Forneci múltiplas formas de criar o projeto
2. Detalhei a estrutura de diretórios
3. Mostrei o código do arquivo principal `CuidaEmpregoApplication.java`
4. Incluí configurações de banco de dados
5. Adicionei dependências no `pom.xml`
6. Incluí comandos úteis e boas práticas

Gostaria que eu detalhe alguma parte específica da configuração do backend?
