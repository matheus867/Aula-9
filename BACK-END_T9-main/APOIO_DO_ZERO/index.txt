<?php
session_start();

// se já existe cookie com nome, pré-preenche
$nome = isset($_COOKIE['nome']) ? $_COOKIE['nome'] : "";
?>
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Simulação de Crédito - Auto Popular</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h2>Simule seu Crédito</h2>
    <form action="simular.php" method="post">
        <label>Nome:</label>
        <input type="text" name="nome" value="<?php echo $nome; ?>" required><br><br>

        <label>Renda mensal (R$):</label>
        <input type="number" name="renda" required><br><br>

        <label>Valor do carro (R$):</label>
        <input type="number" name="valor" required><br><br>

        <label>Parcelas:</label>
        <select name="parcelas">
            <option value="12">12x</option>
            <option value="24">24x</option>
            <option value="36">36x</option>
        </select><br><br>

        <button type="submit">Simular</button>
    </form>
</body>
</html>
