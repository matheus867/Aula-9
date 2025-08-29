<?php
session_start();

if (!isset($_SESSION['resultado'])) {
    echo "<p>Simulação expirada. Volte à página inicial.</p>";
    exit;
}

$res = $_SESSION['resultado'];
?>
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Resultado da Simulação</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h2>Resultado da Simulação</h2>
    <p><b>Nome:</b> <?php echo $res['nome']; ?></p>
    <p><b>Valor do carro:</b> R$ <?php echo number_format($res['valor'],2,',','.'); ?></p>
    <p><b>Parcelas:</b> <?php echo $res['parcelas']; ?>x</p>
    <p><b>Valor de cada parcela:</b> R$ <?php echo number_format($res['parcela'],2,',','.'); ?></p>
    <p><b>Renda declarada:</b> R$ <?php echo number_format($res['renda'],2,',','.'); ?></p>
    <hr>
    <?php if ($res['aprovado']) { ?>
        <p style="color:green;">✅ Parabéns! Crédito aprovado.</p>
    <?php } else { ?>
        <p style="color:red;">❌ Infelizmente o crédito não foi aprovado.</p>
    <?php } ?>

    <a href="index.php">Nova simulação</a>
</body>
</html>
