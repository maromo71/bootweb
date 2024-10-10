# Bootstrap para Desenvolvimento de Aplicação Maven Web com Jakarta EE

Este repositório contém o bootstrap inicial para o desenvolvimento de uma aplicação web utilizando **Maven**, **Jakarta EE**, **Jetty** como servlet container, e **MySQL** como banco de dados. O propósito deste projeto é fornecer uma base sólida para quem deseja começar o desenvolvimento de aplicações corporativas baseadas no ecossistema Jakarta EE, com uma estrutura de projeto configurada e pronta para uso.

Preparado por:  
**Prof. Me. Marcos Roberto de Moraes (Maromo)**  
Faculdade de Engenharia de Computação - Santa Lúcia

## Pré-requisitos

Antes de iniciar o desenvolvimento da aplicação, certifique-se de que você tem os seguintes softwares instalados:

- **JDK 17** (ou versão mais recente)
- **Apache Maven** (versão 3.6 ou superior)
- **MySQL Server** (versão 8.0 ou superior)
- **IDE** (Recomendado: IntelliJ IDEA ou Eclipse com suporte a Jakarta EE)

## Estrutura do Projeto

A estrutura do projeto foi criada utilizando o modelo padrão de um projeto Maven com o seguinte layout:

```
├── src
│   ├── main
│   │   ├── java
│   │   ├── resources
│   │   └── webapp
│   │       ├── WEB-INF
│   │       └── index.jsp
│   └── test
├── pom.xml
└── README.md
```

- O diretório `src/main/webapp` contém os arquivos da interface da aplicação.
- O diretório `src/main/java` deve conter os servlets e classes de back-end.
- O arquivo `pom.xml` está configurado para usar o Jetty como servlet container.

## Passos para Configuração

1. **Clone o repositório:**

git clone https://github.com/maromo71/bootweb.git  
cd seu-repositorio

2. **Configuração do MySQL:**

Certifique-se de que o MySQL esteja instalado e em execução. Crie um banco de dados para a aplicação:

CREATE DATABASE minha_aplicacao;  
CREATE USER 'meu_usuario'@'localhost' IDENTIFIED BY 'minha_senha';  
GRANT ALL PRIVILEGES ON minha_aplicacao.* TO 'meu_usuario'@'localhost';  
FLUSH PRIVILEGES;

Configure o `persistence.xml` ou `datasource` no projeto para que a aplicação se conecte ao banco de dados MySQL.

3. **Configuração do Maven:**

Atualize o arquivo `pom.xml` com as dependências necessárias para o Jetty, Jakarta EE e MySQL.

Exemplo de configuração no `pom.xml` para o Jetty:

<dependencies>
   <!-- Dependências Jakarta EE -->
    <dependency>
        <groupId>jakarta.servlet</groupId>
        <artifactId>jakarta.servlet-api</artifactId>
        <version>6.1.0</version>
        <scope>provided</scope>
    </dependency>
    <dependency>
        <groupId>jakarta.servlet.jsp.jstl</groupId>
        <artifactId>jakarta.servlet.jsp.jstl-api</artifactId>
        <version>3.0.2</version>
    </dependency>

   <!-- Dependência MySQL -->
   <dependency>
       <groupId>mysql</groupId>
       <artifactId>mysql-connector-java</artifactId>
       <version>8.0.34</version>
   </dependency>
</dependencies>

<build>
   <plugins>
      <!-- Plugin Jetty -->
      <plugin>
         <groupId>org.eclipse.jetty</groupId>
         <artifactId>jetty-maven-plugin</artifactId>
         <version>11.0.24</version>
         <configuration>
             <webApp>
                 <contextPath>/</contextPath>
             </webApp>
         </configuration>
      </plugin>
   </plugins>
</build>

4. **Executando o projeto:**

Com todas as dependências configuradas, você pode executar a aplicação localmente com o comando Maven:

mvn clean compile jetty:run

A aplicação estará disponível no navegador em [http://localhost:8080](http://localhost:8080).

## Contribuições

Contribuições para a melhoria deste projeto são bem-vindas. Por favor, faça um fork do repositório e envie um pull request com suas melhorias.

## Licença

Este projeto é licenciado sob a [MIT License](LICENSE).

---

**Prof. Me. Marcos Roberto de Moraes (Maromo)**  
Contato: [professormoraes@gmail.com](mailto:professormoraes@gmail.com)
