function minhaFuncaoManual() {
  // Obtém a planilha ativa
  var planilhaAtiva = SpreadsheetApp.getActiveSpreadsheet();
  
  // Define a aba de origem e destino
  var abaOrigem = planilhaAtiva.getSheetByName('Lista');
  var abaDestino = planilhaAtiva.getSheetByName('Database');

  try {
  //Limpa a página destino
  var totalLinhas = abaDestino.getLastRow();
  var intervaloLimpar = abaDestino.getRange(2, 1, totalLinhas - 1, abaDestino.getLastColumn());
  intervaloLimpar.clear();
    } catch (e) {
    // Se ocorrer uma exceção, capturar e registrar no console
    Logger.log("Ocorreu uma exceção: " + e);
  }

  // Encontrar a última coluna com dados na aba de origem
  var ultimaColuna = abaOrigem.getRange(1, 1, 1, abaOrigem.getLastColumn()).getLastColumn();
  
  //-------------------------------------------------------------//

  // faz um loop para cada coluna
  for (var coluna = 4; coluna <= ultimaColuna; coluna = coluna + 1) {
    
    // Obtém a lista de procedimentos
    var procedimentos = abaOrigem.getRange('B2:B').getValues().filter(String);

    //Obtém a lista de area
    var area = abaOrigem.getRange('A2:A' + procedimentos.length).getValues();
    area.forEach(function(valor, indice) {
      if (valor[0] !== '') {
        ultimoValorValido = valor;
      } else {
        // Se o valor atual for nulo, substitui pelo último valor válido
        area[indice] = ultimoValorValido;
      }
    });
    area[area.length] = area[area.length -1]

    //Obtém a lista de valores
    var valores = abaOrigem.getRange('C2:C').getValues().filter(String);

    //Declara as coberturas e planos
    var plano = abaOrigem.getRange(1 , coluna).getValue()
    var coberturas = abaOrigem.getRange(2, coluna, procedimentos.length, 1).getValues()

    // Obtém a última linha preenchida na coluna A da aba de destino
    var ultimaLinhaDestino = abaDestino.getLastRow() + 1;
    
    // Define o intervalo de destino e cola os dados
    var intervalo = abaDestino.getRange(ultimaLinhaDestino, 1, area.length, 1);
    intervalo.setValues(area);

    // Define o intervalo de destino e cola os dados
    intervalo = abaDestino.getRange(ultimaLinhaDestino, 2, procedimentos.length, 1);
    intervalo.setValues(procedimentos);

    // Define o intervalo de destino e cola os dados
    intervalo = abaDestino.getRange(ultimaLinhaDestino, 3, valores.length, 1);
    intervalo.setValues(valores);

    //insere os planos
    intervalo = abaDestino.getRange(ultimaLinhaDestino, 4, procedimentos.length, 1);
    intervalo.setValue(plano);

    //insere as coberturas
    intervalo = abaDestino.getRange(ultimaLinhaDestino, 5, procedimentos.length, 1);
    intervalo.setValues(coberturas);
  }
  
  //---------------------------------------//

  //deleta linhas sem cobertura de plano
  var ultimaLinha = abaDestino.getLastRow();
  var valores = abaDestino.getRange(1, 5, ultimaLinha, 1).getValues(); // Coluna C, índice 3

  // Loop reverso para evitar problemas com a exclusão de linhas durante a iteração
  for (var i = ultimaLinha; i > 0; i--) {
    // Verifica se o valor na coluna C é nulo
    if (valores[i - 1][0] === null || valores[i - 1][0] === "") {
      // Se sim, exclui a linha
      abaDestino.deleteRow(i);
    }
  }
}

function onOpen() {
  var spreadsheet = SpreadsheetApp.getActiveSpreadsheet();
  var menuItems = [
    { name: 'Executar', functionName: 'minhaFuncaoManual' }
  ];
  spreadsheet.addMenu('Atualizar', menuItems);
}
