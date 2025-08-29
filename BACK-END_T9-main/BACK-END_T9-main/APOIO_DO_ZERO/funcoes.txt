<?php
function calcularParcela($valor, $parcelas) {
    $juros = 0.02; // 2% ao mês fixo
    $valorComJuros = $valor * pow((1+$juros), $parcelas/12);
    return round($valorComJuros / $parcelas, 2);
}
