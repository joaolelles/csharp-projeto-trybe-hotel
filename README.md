# Trybe Hotel

Boas-vindas ao repositório do projeto Trybe Hotel
  
<details>
<summary><strong>🧑‍💻 O que deverá ser desenvolvido</strong></summary>

A empresa começou a desenvolver um software de booking de várias redes de hotéis.
A missão inicial é começar a desenvolver uma API responsável pelo controle de cidades, hotéis e quartos disponíveis para realizar reservas.
(Aplicação desenvolvida durante o curso da eletiva de C# na Trybe).

</details>
  
<details>
  <summary><strong>📝 Habilidades a serem trabalhadas </strong></summary>

- Entender do funcionamento do ASP.NET e como ele se integra ao C#.
- Entender do funcionamento do banco de dados.
- Criar operações de manipulação de banco de dados em uma API.


</details>


## Orientações
---

<details>
  <summary><strong>‼️ Antes de começar a desenvolver</strong></summary><br />

  1. Clone o repositório

  2. Instale as dependências
  
  - Entre na pasta `src/`.
  - Execute o comando: `dotnet restore`.
  
  3. Crie uma branch a partir da branch `master`

  4. Adicione as mudanças ao _stage_ do Git e faça um `commit`

  5. Adicione a sua branch com o novo `commit` ao repositório remoto

  6. Crie um novo `Pull Request` _(PR)_

</details>

<details>
  <summary><strong>🎛 Linter</strong></summary><br />

  Usaremos o [NetAnalyzer](https://docs.microsoft.com/pt-br/dotnet/fundamentals/code-analysis/overview) para fazer a análise estática do seu código.

  Este projeto já vem com as dependências relacionadas ao _linter_ configuradas no arquivo `.csproj`.

  O analisador já é instalado pelo plugin da `Microsoft C#` no `VSCode`. Para isso, basta fazer o download do [plugin](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) e instalá-lo.
</details>

<details>
  <summary><strong>🛠 Testes</strong></summary><br />

  O .NET já possui sua própria plataforma de testes.
  
  Este projeto já vem configurado e com suas dependências.

  ### Executando todos os testes

  Para executar os testes com o .NET, execute o comando dentro do diretório do seu projeto `src`!

  ```
  dotnet test
  ```

  ### Executando um teste específico

  Para executar um teste específico, basta executar o comando `dotnet test --filter Name~TestMethod1`.

  :warning: **Importante:** o comando irá executar testes cujo nome contém `TestMethod1`.

  :warning: **O avaliador automático não necessariamente avalia seu projeto na ordem em que os requisitos aparecem no readme. Isso acontece para deixar o processo de avaliação mais rápido. Então, não se assuste se isso acontecer, ok?**

  ### Outras opções para testes
  - Algumas opções que podem lhe ajudar são:
    -  `-?|-h|--help`: exibe a descrição completa de como utilizar o comando.
    -  `-t|--list-tests`: lista todos os testes, ao invés de executá-los.
    -  `-v|--verbosity <LEVEL>`: define o nível de detalhe na resposta dos testes.
      - `q | quiet`
      - `m | minimal`
      - `n | normal`
      - `d | detailed`
      - `diag | diagnostic`
      - Exemplo de uso: 
         ```
           dotnet test -v diag
         ```
         ou
         ```            
           dotnet test --verbosity=diagnostic
         ``` 
</details>

## Requisitos do projeto

Você está iniciando o desenvolvimento de uma API que será utilizada em uma aplicação de booking de várias redes de hotéis.

Para iniciar o desenvolvimento, você desenvolverá algumas rotas das entidades acerca das cidades, hotéis e quartos que servirão para, no futuro, realizar o booking de pessoas clientes.

No intuito de auxiliar o desenvolvimento, o time de produto já disponibilizou o diagrama de entidade-relacionamento e o time de DevOps disponibilizou um container na qual você poderá utilizar um banco de dados.

O sistema está dividido em diretórios específicos para auxiliar na organização e desenvolvimento do projeto.

- `Controllers/`: Este diretório armazena os arquivos com as lógicas dos controllers da aplicação. Os métodos a serem desenvolvidos estão prontos mas sem implementação alguma, o que você desenvolverá ao longo do projeto.
<br />

- `Models/`: Este diretório armazena os arquivos com as models do banco de dados. As models `City`, `Hotel` e `Room` serão as instruções para as tabelas `Cities`, `Hotels` e `Rooms`. Lembre-se, o nome da tabela não é dado pelo nome da model mas sim pelo nome do `DBSet<model>` presente no contexto.
<br />

- `DTO/`: Este diretório armazena as classes de DTO. Algumas rotas esperam as `responses` baseadas nestes DTOs. Você pode conferir isso pelo requisito do projeto e pelo retorno dos métodos dos `repositories`.
<br />

- `Repository/`: Este diretório armazena as lógicas que farão a interação com o banco de dados. Os métodos de cada requisito já estão criados e você deverá incluir a implementação de cada um desses métodos respeitando o retorno do DTO. Além disso, você terá o arquivo `TrybeHotelContext` com o contexto para a conexão com o banco de dados. Todos os `repository` e o `context` possuem interfaces que estão nesse diretório e fornecem o contrato para essas classes.
<br />

<details id='der'>
  <summary><strong>🎲 Banco de Dados</strong></summary>
  <br/>

  Para o desenvolvimento, o time de produto disponibilizou um *Diagrama de Entidade-Relacionamento (DER)* para construir a modelagem do banco de dados. Com essa imagem você já consegue saber:
  - Como nomear suas tabelas e colunas;
  - Quais são os tipos de suas colunas;
  - Relações entre tabelas.

    ![banco de dados](img/der.png)

  O diagrama infere 03 tabelas:
  - ***Cities***: tabela que armazenará um conjunto de cidades nas quais os hotéis estão localizados.
  - ***Hotels***: tabela que armazenará os hotéis da nossa aplicação. Note que informamos o `CityId`, atributo que armazenará o id da cidade.
  - ***Rooms***: tabela que armazenará os quartos de cada hotel da nossa aplicação. Note que informamos o `HotelId`, atributo que armazenará o id do hotel.

  Acerca dos relacionamentos, pelo diagrama de entidade-relacionamento temos:
  - Uma cidade pode ter vários hotéis.
  - Um hotel pode ter vários quartos.

  ⚠️ **Você poderá criar migrations para visualizar o banco de dados**

</details>

<details>
<summary><strong>🐳 Docker</strong></summary><br />

Para auxiliar no desenvolvimento, este projeto possui um arquivo do docker compose para subir um serviço do banco de dados `Azure Data Studio`. Este banco de dados possui a mesma arquitetura do `SQL Server`.

Para subir o serviço, utilize o comando:

```shell
docker-compose up -d --build
```

Para conectar ao seu sistema de gerenciamento de banco de dados, utilize as seguintes credenciais:

- `Server`: localhost
- `User`: sa
- `Password`: TrybeHotel12!
- `Database`: TrybeHotel
- `Trust server certificate`: true

Para criar o contexto do banco de dados na sua aplicação, utilize como connection string:

```csharp
var connectionString = "Server=localhost;Database=TrybeHotel;User=SA;Password=TrybeHotel12!;TrustServerCertificate=True";
```

⚠️ ** Essa connection string poderá ser utilizada no requisito 1 **

</details>

### 1. Implemente as models da aplicação

<details>
  <summary><strong>Mais informações:</strong></summary>

  Implemente os arquivos do diretório `/src/TrybeHotel/Models/`

  <details>
    <summary>Implemente a model <code>City</code></summary>
    <br />
City representará as cidades da aplicação e deverá conter os seguintes campos:
- `CityId`: Chave primária (int)
- `Name`: string
Cada cidade tem vários hotéis. A propriedade de navegação para `Hotel` deve se chamar `Hotels` (anulável).

Em caso de dúvidas, consulte o [diagrama de entidade-relacionamento](#der)
  </details>

<details>
    <summary>Implemente a model <code>Hotel</code></summary>
    <br />

Hotel representará os hotéis da aplicação e deverá conter os seguintes campos:
- `HotelId`: Chave primária (int)
- `Name`: string
- `Address`: string
- `CityId`: Chave estrangeira para a model `City` (int)
Cada hotel tem vários quartos. A propriedade de navegação para `Room` deve se chamar `Rooms` (anulável).
Cada hotel tem apenas uma cidade. A propriedade de navegação para `City` deve se chamar `City` (anulável).

Em caso de dúvidas, consulte o [diagrama de entidade-relacionamento](#der)
  </details>

  <details>
    <summary>Implemente a model <code>Room</code></summary>
    <br />

Room representará os quartos da aplicação e deverá conter os seguintes campos:
- `RoomId`: Chave primária (int)
- `Name`: string
- `Capacity`: int
- `Image`: string
- `HotelId`: Chave estrangeira para a model `Hotel`(int).
Cada quarto tem apenas um hotel. A propriedade de navegação para `Hotel` deve se chamar `Hotel` (anulável).

Em caso de dúvidas, consulte o [diagrama de entidade-relacionamento](#der)
  </details>

  <details>
    <summary>Implemente o contexto do banco de dados</summary>
    <br />

Finalize a implementação do contexto da aplicação no arquivo `src/TrybeHotel/Repository/TrybeHotelContext.cs`.

O contexto deverá ter todas as models da aplicação com os nomes `Cities`, `Hotels` e `Rooms`.

Faça um `override` do método `OnConfiguring` para o contexto se conectar ao seu banco de dados local.

Caso você queira executar o seu projeto para testar localmente, utilize o arquivo docker-compose.yml com um banco SqlServer. Caso você queira usar essa base, tenha o Docker e o docker-compose instalado na sua máquina!

Caso utilize este banco, configure a sua connectionString como:

```csharp
var connectionString = "Server=localhost;Database=TrybeHotel;User=SA;Password=TrybeHotel12!;TrustServerCertificate=True";
```

Você pode criar as tabelas do banco de dados atráves dos comandos `dotnet ef migrations add InitialCreate` e `dotnet ef database update`. Caso você execute esse comando, certifique-se de que o CLI do Entity Framework esteja instalado na sua máquina!
  </details>

<br />

**O que será testado:**

- Será testado que todas as models foram implementadas corretamente.
- Será testado que as models possuem as chaves primárias e estrangeiras necessárias.

</details>

### 2. Desenvolva o endpoint GET /city

<details>
  <summary><strong>Mais informações:</strong></summary>

- Este endpoint será responsável por listar todas as cidades.
- Implemente a lógica da sua controller no método `GetCities()` do arquivo `src/TrybeHotel/Controllers/CityController.cs`.
- Implemente a lógica de interação ao banco de dados no método `GetCities()` do arquivo `src/TrybeHotel/Repository/CityRepository.cs`.
- A sua repository retorna um tipo `CityDto` que deverá ser implementado no arquivo `src/TrybeHotel/Dto/CityDto.cs`. A sua classe de DTO deve seguir o formato da response da requisição. 
<br />

👀 **De olho na dica:** Monte o retorno do seu repository com os conhecimentos de `LINQ` e `DTO` já obtidos.
<br />

👀 **De olho na dica 2:** Para converter qualquer tipo de coleção no tipo de coleção `List`, utilize o método `ToList()`.

<br />

- O endpoint deve ser acessível através da URL `/city` e deve ser do tipo `GET`;
- O corpo da requisição é vazio.
- A resposta deve ser o status `200`.
- O corpo da resposta deve seguir o formato abaixo:

```json
[
    {
	    "cityId": 1,
	    "name": "Rio Branco"
    },

  /*...*/
]
```

**O que será testado:**

- Será testado que, quando solicitada a requisição, a mesma informe os dados correspondentes do banco de dados.
- Será testado que o status de retorno será `200`.
- Será testado que o corpo da resposta segue o padrão esperado.

</details>

### 3. Desenvolva o endpoint POST /city

<details>
  <summary><strong>Mais informações:</strong></summary>

- Este endpoint será responsável por inserir uma nova cidade.
- Implemente a lógica da sua controller no método `PostCity()` do arquivo `src/TrybeHotel/Controllers/CityController.cs`.
- Implemente a lógica de interação ao banco de dados no método `AddCity()` do arquivo `src/TrybeHotel/Repository/CityRepository.cs`.
- A sua repository retorna um tipo `CityDto` que deverá ser implementado no arquivo `src/TrybeHotel/Dto/CityDto.cs`. A sua classe de DTO deve seguir o formato da response da requisição. 
<br />

👀 **De olho na dica:** Monte o retorno do seu repository com os conhecimentos de `LINQ` e `DTO` já obtidos.
<br />

👀 **De olho na dica 2:** Para obter um único elemento de uma coleção, você pode obter o primeiro com o método `First()`. Exemplo: `coleção.First()`.

<br />

- O endpoint deve ser acessível através da URL `/city` e deve ser do tipo `POST`;
- O corpo da requisição deve seguir o padrão abaixo

```json
{
	"Name": "Rio de Janeiro"
}
```

- A resposta deve ser o status `201`.
- O corpo da resposta deve seguir o formato abaixo:

```json

{
	  "cityId": 2,
	  "name": "Rio de Janeiro"
},
```

**O que será testado:**

- Será testado que, quando solicitada a requisição, a mesma insira no banco de dados e retorne de acordo com o modelo
- Será testado que o status de retorno será `201`.
- Será testado que o corpo da resposta segue o padrão esperado.

</details>

### 4. Desenvolva o endpoint GET /hotel

<details>
  <summary><strong>Mais informações:</strong></summary>

- Este endpoint será responsável por listar todos os hotéis.
- Implemente a lógica da sua controller no método `GetHotels()` do arquivo `src/TrybeHotel/Controllers/HotelController.cs`.
- Implemente a lógica de interação ao banco de dados no método `GetHotels()` do arquivo `src/TrybeHotel/Repository/HotelRepository.cs`.
- A sua repository retorna um tipo `HotelDto` que deverá ser implementado no arquivo `src/TrybeHotel/Dto/HotelDto.cs`. A sua classe de DTO deve seguir o formato da response da requisição. 
<br />

👀 **De olho na dica:** Monte o retorno do seu repository com os conhecimentos de `LINQ` e `DTO` já obtidos.
<br />

👀 **De olho na dica 2:** Para converter qualquer tipo de coleção no tipo de coleção `List`, utilize o método `ToList()`.

<br />

- O endpoint deve ser acessível através da URL `/hotel` e deve ser do tipo `GET`;
- O corpo da requisição é vazio.
- A resposta deve ser o status `200`.
- O corpo da resposta deve seguir o formato abaixo:

```json
[
    {
		  "hotelId": 1,
		  "name": "Trybe Hotel SP",
		  "address": "Avenida Paulista, 1400",
		  "cityId": 1,
		  "cityName": "São Paulo"
	  },

  /*...*/
]
```

**O que será testado:**

- Será testado que, quando solicitada a requisição, a mesma informe os dados correspondentes do banco de dados.
- Será testado que o status de retorno será `200`.
- Será testado que o corpo da resposta segue o padrão esperado.

</details>

### 5. Desenvolva o endpoint POST /hotel

<details>
  <summary><strong>Mais informações:</strong></summary>

- Este endpoint será responsável por inserir um novo hotel.
- Implemente a lógica da sua controller no método `PostHotel()` do arquivo `src/TrybeHotel/Controllers/HotelController.cs`.
- Implemente a lógica de interação ao banco de dados no método `AddHotel()` do arquivo `src/TrybeHotel/Repository/HotelRepository.cs`.
- A sua repository retorna um tipo `HotelDto` que deverá ser implementado no arquivo `src/TrybeHotel/Dto/HotelDto.cs`. A sua classe de DTO deve seguir o formato da response da requisição. 
<br />

👀 **De olho na dica:** Monte o retorno do seu repository com os conhecimentos de `LINQ` e `DTO` já obtidos.
<br />

👀 **De olho na dica 2:** Para obter um único elemento de uma coleção, você pode obter o primeiro com o método `First()`. Exemplo: `coleção.First()`.

<br />

- O endpoint deve ser acessível através da URL `/hotel` e deve ser do tipo `POST`;
- O corpo da requisição deve seguir o padrão abaixo

```json
{
	"Name":"Trybe Hotel RJ",
	"Address":"Avenida Atlântica, 1400",
	"CityId": 2
}
```

- A resposta deve ser o status `201`.
- O corpo da resposta deve seguir o formato abaixo:

```json
{
	"hotelId": 2,
	"name": "Trybe Hotel RJ",
	"address": "Avenida Atlântica, 1400",
	"cityId": 2,
	"cityName": "Rio de Janeiro"
}
```

**O que será testado:**

- Será testado que, quando solicitada a requisição, a mesma insira no banco de dados e retorne de acordo com o modelo
- Será testado que o status de retorno será `201`.
- Será testado que o corpo da resposta segue o padrão esperado.

</details>


### 6. Desenvolva o endpoint GET /room/:hotelId

<details>
  <summary><strong>Mais informações:</strong></summary>

- Este endpoint será responsável por listar todos os quartos de um determinado hotel
- Implemente a lógica da sua controller no método `GetRoom()` do arquivo `src/TrybeHotel/Controllers/RoomController.cs`.
- Implemente a lógica de interação ao banco de dados no método `GetRooms()` do arquivo `src/TrybeHotel/Repository/RoomRepository.cs`.
- A sua repository retorna um tipo `RoomDto` que deverá ser implementado no arquivo `src/TrybeHotel/Dto/RoomDto.cs`. A sua classe de DTO deve seguir o formato da response da requisição. 
<br />

👀 **De olho na dica:** Monte o retorno do seu repository com os conhecimentos de `LINQ` e `DTO` já obtidos.
<br />

👀 **De olho na dica 2:** Para converter qualquer tipo de coleção no tipo de coleção `List`, utilize o método `ToList()`.

<br />

- O endpoint deve ser acessível através da URL `/room/:hotelId` e deve ser do tipo `GET`;
- O corpo da requisição é vazio.
- A resposta deve ser o status `200`.
- O corpo da resposta deve seguir o formato abaixo:

```json
[
    {
		  "roomId": 1,
		  "name": "Suite básica",
		  "capacity": 2,
		  "image": "image suite",
		  "hotel": {
  			"hotelId": 1,
			  "name": "Trybe Hotel SP",
			  "address": "Avenida Paulista, 1400",
			  "cityId": 1,
			  "cityName": "São Paulo"
		  }
	  },

  /*...*/
]
```

**O que será testado:**

- Será testado que, quando solicitada a requisição, a mesma informe os dados correspondentes do banco de dados.
- Será testado que o status de retorno será `200`.
- Será testado que o corpo da resposta segue o padrão esperado.

</details>

### 7. Desenvolva o endpoint POST /room


<details>
  <summary><strong>Mais informações:</strong></summary>

- Este endpoint será responsável por inserir um novo quarto a um hotel.
- Implemente a lógica da sua controller no método `PostRoom()` do arquivo `src/TrybeHotel/Controllers/RoomController.cs`.
- Implemente a lógica de interação ao banco de dados no método `AddRoom()` do arquivo `src/TrybeHotel/Repository/RoomRepository.cs`.
- A sua repository retorna um tipo `RoomDto` que deverá ser implementado no arquivo `src/TrybeHotel/Dto/RoomDto.cs`. A sua classe de DTO deve seguir o formato da response da requisição. 
<br />

👀 **De olho na dica:** Monte o retorno do seu repository com os conhecimentos de `LINQ` e `DTO` já obtidos.
<br />

👀 **De olho na dica 2:** Para obter um único elemento de uma coleção, você pode obter o primeiro com o método `First()`. Exemplo: `coleção.First()`.

<br />

- O endpoint deve ser acessível através da URL `/room` e deve ser do tipo `POST`;
- O corpo da requisição deve seguir o padrão abaixo

```json
{
	"Name":"Suite básica",
	"Capacity":2,
	"Image":"image suite",
	"HotelId": 1
}
```

- A resposta deve ser o status `201`.
- O corpo da resposta deve seguir o formato abaixo:

```json
{
	"roomId": 1,
	"name": "Suite básica",
	"capacity": 2,
	"image": "image suite",
	"hotel": {
		"hotelId": 1,
		"name": "Trybe Hotel SP",
		"address": "Avenida Paulista, 1400",
		"cityId": 1,
		"cityName": "São Paulo"
	}
}
```

**O que será testado:**

- Será testado que, quando solicitada a requisição, a mesma insira no banco de dados e retorne de acordo com o modelo
- Será testado que o status de retorno será `201`.
- Será testado que o corpo da resposta segue o padrão esperado.
</details>

### 8. Desenvolva o endpoint DELETE /room/:roomId

<details>
  <summary><strong>Mais informações:</strong></summary>

- Este endpoint será responsável por deletar um determinado quarto.
- Implemente a lógica da sua controller no método `Delete()` do arquivo `src/TrybeHotel/Controllers/RoomController.cs`.
- Implemente a lógica de interação ao banco de dados no método `DeleteRoom()` do arquivo `src/TrybeHotel/Repository/RoomRepository.cs`.
- O endpoint deve ser acessível através da URL `/room/:roomId` e deve ser do tipo `DELETE`;
- O corpo da requisição é vazio.
- A resposta deve ser o status `204`.

**O que será testado:**

- Será testado que, quando solicitada a requisição, a mesma faça a exclusão solicitada no banco de dados.
- Será testado que o status de retorno será `204`.

</details>

### 9. Desenvolva testes que cubram no mínimo 40% de linhas

<details>
  <summary><strong>Mais informações:</strong></summary>

- Desenvolva testes de integração que cubram 40% das linhas de código.
- Os testes devem ser implementados no arquivo `src/TrybeHotel.Test/IntegrationTest.cs`
- Este arquivo possui uma classe chamada `IntegrationTest`. Cada método dessa classe é um teste diferente.
- O construtor da classe `IntegrationTest` cria um `context` em memória de um banco de dados que será utilizado nos testes. Verifique neste construtor quais são as cidades, hotéis e quartos disponíveis no banco de dados que será utilizado no teste 👀.
- Este arquivo de testes já possui um método `TestGet` que testa a rota GET `/room`. Utilize o mesmo como exemplo para criar novos métodos e testar outras rotas.

**O que será testado:**

- Será avaliado que os testes cubram 40% das linhas de código.

</details>

