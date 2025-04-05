# Lab03Multiplataforma

## Ejercicio 1: Usuario y Autenticación

```dart
// Definimos la clase base Usuario
class Usuario {
  String nombre;
  String email;
  String contrasena;

  // Constructor de la clase Usuario
  Usuario(this.nombre, this.email, this.contrasena);
}

// Mixin de Autenticación que contiene el método iniciarSesion
mixin Autenticacion on Usuario {
  void iniciarSesion() {
    if (this.email.isNotEmpty && this.contrasena.isNotEmpty) {
      print('Iniciando sesión para el usuario ${this.nombre}...');
      print('Sesión iniciada con éxito.');
    } else {
      print('Error: Email o contraseña vacíos.');
    }
  }
}

// Clase UsuarioAutenticado que hereda de Usuario y utiliza el mixin Autenticacion
class UsuarioAutenticado extends Usuario with Autenticacion {
  UsuarioAutenticado(String nombre, String email, String contrasena) 
      : super(nombre, email, contrasena);
}

void main() {
  // Crear un objeto de la clase UsuarioAutenticado
  var usuario = UsuarioAutenticado('Juan Pérez', 'juan.perez@example.com', 'contraseña123');
  
  // Invocar el método iniciarSesion del mixin Autenticacion
  usuario.iniciarSesion();
}
------------------------------------------------------------------------------------
`## Ejercicio 5:Sistema de Votación

// Clase base Votante
class Votante {
  String nombre;
  int edad;
  bool haVotado;

  // Constructor de la clase Votante
  Votante(this.nombre, this.edad, {this.haVotado = false});
}

// Mixin ValidacionVoto
mixin ValidacionVoto on Votante {
  // Método para validar si el votante puede votar (por edad)
  void validarVoto() {
    if (this.edad >= 18) {
      print('$nombre es elegible para votar.');
    } else {
      print('$nombre no es elegible para votar.');
    }
  }
}

// Clase VotanteValido que hereda de Votante y usa el mixin ValidacionVoto
class VotanteValido extends Votante with ValidacionVoto {
  VotanteValido(String nombre, int edad) : super(nombre, edad);
}

void main() {
  // Crear un objeto de tipo VotanteValido
  var votante = VotanteValido('Carlos López', 20);
  
  // Validar el derecho a votar
  votante.validarVoto();

  // Crear otro objeto con edad no válida
  var votante2 = VotanteValido('Ana García', 16);
  
  // Validar el derecho a votar
  votante2.validarVoto();
}
