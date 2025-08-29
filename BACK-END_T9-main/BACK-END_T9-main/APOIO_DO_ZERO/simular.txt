<?php
session_start();
include "includes/funcoes.php";

// recebe dados do formulário
$nome    = $_POST['nome'];
$renda   = $_POST['renda'];
$valor   = $_POST['valor'];
$parcelas = $_POST['parcelas'];

// cria cookie para lembrar nome por 1 dia
setcookie("nome", $nome, time()+86400);

// usa função para calcular parcela
$parcela = calcularParcela($valor, $parcelas);

// regra simples: parcela não pode ultrapassar 30% da renda
$limite = $renda * 0.3;
$aprovado = ($parcela <= $limite);

// salva em sessão
$_SESSION['resultado'] = [
    "nome" => $nome,
    "valor" => $valor,
    "parcelas" => $parcelas,
    "parcela" => $parcela,
    "renda" => $renda,
    "aprovado" => $aprovado
];

// redireciona para resultado
header("Location: resultado.php");
exit;
