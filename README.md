# Apresentação

Programa exemplo desenvolvido em Flutter durante o curso de Firebase Crashlytics da [Alura](https://www.alura.com.br/).
É apresentado nesta aplicação como configurar, e usar os recursos do Firebase Crashlytics para monitorar sua aplicação e obter uma relatório completo sobre os bugs de sua aplicação, e dados de utilização. 


# Requisitos

Para executar o programa é necessário:

* Ter instalado o sdk do Flutter baixado no seu sistema operacional. 
* [online documentation](https://docs.flutter.dev/)
* [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
* [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)
* Emulador usando o Android Studio ou um telefone celular.
* Ter Android Studio ou IntelliJ instalados.


# Recursos abordados

* Widgets.
* Listas.
* Sqlite.
* Navegação entre paginas.
* Floatbutton.


# Compilar e rodar

Abrir pelo IntelliJ ou Android Studio e rodar em um emulador ou em próprio equiapmento mobile.


# bytebank web API

Deve ser rodado esse servidor  Web API desenvolvido em Sprint Boot para cosumo do APP.
A Web API oferece as seguintes funcionalidades:

- Listagem e cadastro de transações.

Para executar deve  rodar pelo prompt:  java -jar server.jar
Foi desenvolvido e dado build  com base no Java 8, portanto é recomendado usar o mesmo, para que tudo funcione conforme o esperado.
Por padrão o Spring Boot vai rodar a aplicação na porta `8080` e vai configurar a senha padrão no valor `1000` para salvar transações.

Caso queria modificar ambos valores execute o arquivo da seguinte maneira:

```
java -jar server.jar --server.port=8081 --user.password=2000


Exemplos de uso da api:

Para acessar as funcionalidades foram disponibilizados os seguintes end-points:

- `/transactions`:
  - **GET**: Listagem:
    - O resultado é ordenado pela data e hora da criação em ordem crescente.

  ```
  // response example
  [
      {
          "id": "b9663ef3-3749-400e-be8f-1280db94aac8",
          "value": 200.00,
          "contact": {
              "name": "gui",
              "accountNumber": 1000
          },
          "dateTime": "2019-11-06 12:57:23"
      },
      {
          "id": "d1bf689c-caa2-4e45-b1fc-5a90b10d6d48",
          "value": 200.00,
          "contact": {
              "name": "gui",
              "accountNumber": 1500
          },
          "dateTime": "2019-11-06 12:57:37"
      }
  ]
  ```

  - **POST**: Inserção:
    - Para salvar a transação é necessário o envio do *header* `password` conforme o valor configurado na aplicação:
      - Caso não seja enviado, é retornado `400 BAD REQUEST`;
      - Caso falhar na autenticação `401 UNAUTHORIZED`.
    - Não é possível alterar a transação, caso haja a tentativa é retornado `409 CONFLICT`.

  ```
  // request body example
  {
    	"value": 200.0,
    	"contact": {
    		"name": "gui",
    		"accountNumber": 1000
    	}
  }

  // response example
  {
        "id": "b9663ef3-3749-400e-be8f-1280db94aac8",
        "value": 200.00,
        "contact": {
            "name": "gui",
            "accountNumber": 1000
        },
        "dateTime": "2019-11-06 12:57:23"
  }