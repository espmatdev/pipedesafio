Explicación del pipeline:

Parametros: Se definen tres parámetros de entrada: NOMBRE, APELLIDO y DEPARTAMENTO.

Validar Datos de Entrada: Se valida que el nombre y el apellido no estén vacíos.

Crear Usuario:

Se genera el login combinando el nombre y el apellido en minúsculas.

Se genera un password temporal usando UUID.

Se ejecutan comandos shell para:

Crear el usuario con su respectivo grupo y shell.

Asignar el password temporal al usuario.

Forzar el cambio de password en el primer login.

Se muestran en consola el login y el password temporal.